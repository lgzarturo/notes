# python-sqlalchemy

Copiar una base de datos a otra usando SQLAlchemy

```python
from sqlalchemy import create_engine, MetaData, event
from sqlalchemy.sql import sqltypes

#  Requires SQLALCHEMY 1.4+
src_engine = create_engine("sqlite:///mydb.sqlite")
src_metadata = MetaData(bind=src_engine)
exclude_tables = ('sqlite_master', 'sqlite_sequence', 'sqlite_temp_master')

tgt_engine = create_engine("postgresql+psycopg2://@localhost/ngas")
tgt_metadata = MetaData(bind=tgt_engine)

@event.listens_for(src_metadata, "column_reflect")
def genericize_datatypes(inspector, tablename, column_dict):
   column_dict["type"] = column_dict["type"].as_generic(allow_nulltype=True)     

tgt_conn = tgt_engine.connect()
tgt_metadata.reflect()

# drop all tables in target database
for table in reversed(tgt_metadata.sorted_tables):
   if table.name not in exclude_tables:
      print('dropping table =', table.name)
      table.drop()

# # Delete all data in target database
# for table in reversed(tgt_metadata.sorted_tables):
#    table.delete()

tgt_metadata.clear()
tgt_metadata.reflect()
src_metadata.reflect()

# create all tables in target database
for table in src_metadata.sorted_tables:
   if table.name not in exclude_tables:
      table.create(bind=tgt_engine)

# refresh metadata before you can copy data
tgt_metadata.clear()
tgt_metadata.reflect()

# Copy all data from src to target
for table in tgt_metadata.sorted_tables:
   src_table = src_metadata.tables[table.name]
   stmt = table.insert()
   for index, row in enumerate(src_table.select().execute()):
      print("table =", table.name, "Inserting row", index)
      stmt.execute(row._asdict())
```

Transferir datos de una tabla a otra

```python
from sqlalchemy.orm import Session
from sqlalchemy import create_engine
from sqlalchemy.ext.automap import automap_base

old_base = automap_base()
old_engine = create_engine("<OLD_DB_URI>", echo=True)
old_base.prepare(old_engine, reflect=True)
TableOld = old_base.classes.table_old
old_session = Session(old_engine)

new_base = automap_base()
new_engine = create_engine("<NEW_DB_URI>", echo=True)
new_base.prepare(new_engine, reflect=True)
TableNew = old_base.classes.table_new
new_session = Session(new_engine)

# here you can write your queries
old_table_results = old_session.query(TableOld).all()
new_data = []
for result in old_table_results:
    new = TableNew()
    new.id = result.id
    new.name = result.name
    new_data.append(new)
new_session.bulk_save_objects(new_data)
new_session.commit()
```

Ejemplo: [insertar datos de forma masiva][1]

Otro método para copiar datos entre tablas

```python
type_str = type('str')
type_datetime = type(datetime.datetime.now())
type_int = type(1)
type_float = type(1.0)
type_None = type(None)
 
 
#todo: handle blob data type
 
def convert2str(record):
    res = []
    for item in record:
        if type(item)==type_None:
            res.append('NULL')
        elif type(item)==type_str:
            res.append('"'+item+'"')
        elif type(item)==type_datetime:
            res.append('"'+str(item)+'"')
        else:  # for numeric values
            res.append(str(item))
    return ','.join(res)
 
 
 
def copy_table(tab_name, src_cursor, dst_cursor):
    sql = 'select * from %s'%tab_name
    src_cursor.execute(sql)
    res = src_cursor.fetchall()
    cnt = 0
    for record in res:
        val_str = convert2str(record)
        try:
            sql = 'insert into %s values(%s)'%(tab_name, val_str)
            dst_cursor.execute(sql)
            cnt += 1
        except:
            print cnt, val_str
    return cnt
```

Clonar tablas 

```python
# define engines/connections/metadata
source = create_engine(<connection string>)
source_meta = MetaData()
source_meta.reflect(bind=source)
source_connection = source.connect()
destination = create_engine(<connection string>)
dest_meta = MetaData()
dest_meta.reflect(bind=destination)
dest_connection = destination.connect()

# declare tables
src_table = Table('table_name', source_meta)
dest_table = Table('table_name', dest_meta)

# truncate destination table
print("truncating table " + table)
dest_connection.execution_options(autocommit = True).execute("truncate table " + table)

# select and insert loop
sel = src_table.select()
res = source_connection.execute(sel)
for row in res:
	# Using session
	# DestSession.execute(dest_table.insert(row)) 
	# DestSession.commit()
    trans = dest_connection.begin()
    dest_table.insert(row)
    trans.commit()
```

Clonar schemas de datos

```python
from sqlalchemy import create_engine, Table, Column, Integer, Unicode, MetaData, String, Text, update, and_, select, func, types

# create engine, reflect existing columns, and create table object for oldTable
srcEngine = create_engine('mysql+mysqldb://username:password@111.111.111.111/database') # change this for your source database
srcEngine._metadata = MetaData(bind=srcEngine)
srcEngine._metadata.reflect(srcEngine) # get columns from existing table
srcTable = Table('oldTable', srcEngine._metadata)

# create engine and table object for newTable
destEngine = create_engine('mysql+mysqldb://username:password@localhost/database') # change this for your destination database
destEngine._metadata = MetaData(bind=destEngine)
destTable = Table('newTable', destEngine._metadata)

# copy schema and create newTable from oldTable
for column in srcTable.columns:
    destTable.append_column(column.copy())
destTable.create()
```

Copiar datos de entre dos tablas idénticas

> Esta no es una buena solución para lidiar con un gran conjunto de datos. Debido a que la inserción es muy lenta, incluso si haces todo lo que encuentras el tamaño de lote óptimo. Así es como funciona un RDBMS. Tienes que usar herramientas de carga masiva como `SQL Loader` para Oracle, `MultiLoad` para Teradata, `COPY` para PostgreSQL

```python
"""
    Copy all records between 2 identical tables using sqlalchemy:
    
    1. generate select query
    2. generate insert query
    3. use batches to reduce resource usage on database servers
"""
import traceback

import sqlalchemy
from sqlalchemy import create_engine, MetaData, Table
from sqlalchemy.orm import sessionmaker
# from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.sql import select
from sqlalchemy.schema import CreateTable

ARRAY_SIZE = 1000

def make_session(connection_string, engine_options={}):
    # options = engine_options or {}
    options = {}
    # todo: what other sqlalchemy supported db not use those properties?
    if not connection_string.startswith('sqlite'):
        options.update(engine_options, convert_unicode=True, coerce_to_decimal=True)

    engine = create_engine(connection_string, **options)
    session = sessionmaker(bind=engine)
    return session(), engine

def copy_table(from_db, from_table, to_db, to_table, 
    from_owner=None, to_owner=None, engine_options={}):
    """
        :param from_db, string, source sqlalchemy db connection url
        :param from_table, string, source table name
        :param to_db, string, destination sqlalchemy db connection url
        :param to_table, string, destination table name
        :param from_owner, optional, string, schema name of source table
        :param to_owner, optional, string, schema name of destination table
    """
    options = {'arraysize': ARRAY_SIZE}
    engine_options.update(options)
    source, sengine = make_session(from_db, engine_options)
    dest, dengine = make_session(to_db, engine_options)
    smeta = MetaData()
    dmeta = MetaData()

    total = 0

    try:
        source_tbl = Table(from_table, smeta, autoload=True, schema=from_owner,autoload_with=sengine)
        dest_tbl = Table(to_table, dmeta, autoload=True, schema=to_owner,autoload_with=dengine)
        # 
        sel_query = select([source_tbl])
        insert_sql = dest_tbl.insert()
        # 
        results = source.execute(sel_query)
        while True:
            recs = results.fetchmany(ARRAY_SIZE)
            _total = len(recs)
            total += _total
            if _total > 0:
                dest.execute(insert_sql, recs)
                dest.commit()
            if _total < ARRAY_SIZE:
                break
        # done
        print(f'{total} records copied from {from_table} to {to_table}')
    except sqlalchemy.exc.NoSuchTableError as e1:
        # traceback.print_exc()
        print(e1)
    except TypeError as e2:
        # traceback.print_exc()
        print(e2)
    except Exception as e3:
        traceback.print_exc()
        print(e3)
    return total
```

Mezclar datos de forma declarativa con SQLAlchemy

```python
from sqlalchemy import MetaData

combined_meta_data = MetaData()

for declarative_base in [Base1, Base2]:
    for (table_name, table) in declarative_base.metadata.tables.items():
        combined_meta_data._add_table(table_name, table.schema, table)
```

Mezclar todas la bases

```python
import gc
from sqlalchemy import MetaData

combined_meta_data = MetaData()

for declarative_base in ([obj for obj in gc.get_objects() if isinstance(obj, DeclarativeMeta)]):
    for (table_name, table) in declarative_base.metadata.tables.items():
        combined_meta_data._add_table(table_name, table.schema, table)
```

La información meta se puede usar para saber las diferencias en la base

```python
from sqlalchemy import create_engine
from alembic.migration import MigrationContext
from alembic.autogenerate import compare_metadata
import pprint

engine = create_engine(...)
migration_context = MigrationContext.configure(engine.connect())

diff = compare_metadata(migration_context, combined_meta_data)
pprint.pprint(diff)
```

Proceso de unir dos tablas usando PostgreSQL

```python
# Creando tablas 
mysql> create database sopython;
Query OK, 1 row affected (0,00 sec)

mysql> create database sopython2;
Query OK, 1 row affected (0,00 sec)

mysql> use sopython
Database changed
mysql> create table foo (foo_id integer not null auto_increment primary key, name text);
Query OK, 0 rows affected (0,05 sec)

mysql> insert into foo (name) values ('heh');
Query OK, 1 row affected (0,01 sec)

mysql> use sopython2
Database changed
mysql> create table bar (bar_id integer not null auto_increment primary key, foo_id integer, foreign key (foo_id) references `sopython`.`foo` (foo_id)) engine=InnoDB;
Query OK, 0 rows affected (0,07 sec)

mysql> insert into bar (foo_id) values (1);
Query OK, 1 row affected (0,01 sec)

# Procesando con python
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.automap import automap_base

Session = sessionmaker()
Base = automap_base()
engine = create_engine('mysql+pymysql://user:pass@:6603/')
Base.prepare(engine, reflect=True, schema='sopython')
Base.prepare(engine, reflect=True, schema='sopython2')
Base.metadata.reflect(engine, schema='sopython')
Base.metadata.reflect(engine, schema='sopython2')
Base.prepare()
Base.metadata.bind = engine
session = Session()
query = session\
	.query(Base.classes.bar)\
	.join(Base.classes.foo)\
	.filter(Base.classes.foo.name == 'heh')
print(query)
query.all()
```

Enlaces de interés
- [Notas técnicas de Bruno Yin’s][2]
- [Programming notes by Paul][3]
- [Mover datos con SQLAlchemy][4]
- [Trabajando con pandas y SQLAlchemy][5]
- [Manejo de datos con Python, SQLite y SQLAlchemy][6]

[1]:	https://docs.sqlalchemy.org/en/20/_modules/examples/performance/bulk_inserts.html
[2]:	https://brunoyin.gitlab.io/post/
[3]:	https://www.paulsprogrammingnotes.com
[4]:	https://www.andrewvillazon.com/move-data-to-db-with-sqlalchemy/
[5]:	https://towardsdatascience.com/work-with-sql-in-python-using-sqlalchemy-and-pandas-cd7693def708
[6]:	https://realpython.com/python-sqlite-sqlalchemy/