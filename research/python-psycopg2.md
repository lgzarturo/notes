# python-psycopg2

Insertar datos en una tabla

```python
import psycopg2

conn = psycopg2.connect(host=pg_credential.hostname,
                        port=pg_credential.port,
                        user=pg_credential.username,
                        password=pg_credential.password,
                        database=pg_credential.path[1:]) # To remove slash

cursor = conn.cursor()
cursor.execute("INSERT INTO a_table (c1, c2, c3) VALUES(%s, %s, %s)", (v1, v2, v3))
conn.commit()
cursor.close()
conn.close()
```

Subir datos a PostgreSQL

```python
import requests
import pandas as pd
import psycopg2


# Getting Data
url = 'https://jsonplaceholder.typicode.com/users'

response = requests.get(url)
json_response = response.json()
df = pd.json_normalize(json_response)

# Creating a table schema
df.columns = [item.lower().replace(" ", "_").replace(".", "_") for item in df.columns]
print(df.columns)

# Replacements dictionary to map pandas dtypes to SQL dtypes
replacements = {
    'object': 'varchar',
    'float64': 'float',
    'int64': 'int',
    'datetime64': 'timestamp',
    'timedelta64[ns]': 'varchar'
}

col_str = ", ".join("{} {}".format(n, d) for (n, d) in zip(df.columns, df.dtypes.replace(replacements)))


# Save df to csv
df.to_csv('post_users.csv', header=df.columns, index=False, encoding='utf-8')
print('csv file created')

# db connection
host = 'IP_Address'
dbname = 'database_name'
user = 'username'
password = 'password'

conn = None


try:
    conn_str = "host=%s dbname=%s user=%s password=%s" % (host, dbname, user, password)
    with psycopg2.connect(conn_str) as conn:
        print("PostgreSQL server information")
        print(conn.get_dsn_parameters(), "\n")

        # Cursor
        with conn.cursor() as cur:
            print('database opened successfully')

            # Drop table if exists
            cur.execute("DROP TABLE IF EXISTS post_users_test")

            # Create table
            cur.execute("CREATE TABLE post_users_test (%s)" % col_str)
            print('table created successfully')

            # Preparing to upload csv to db:
            # Open csv file, and save it as an object
            csv_file = open('post_users.csv')
            print('file opened in memory')

            # SQL copy statement
            SQL = """
            COPY post_users_test FROM STDIN WITH
                CSV
                HEADER
                DELIMITER AS ','
            """

            cur.copy_expert(sql=SQL, file=csv_file)
            print('file copied to db')

            # Checking the data from PostgreSQL 
            cur.execute("SELECT * FROM post_users_test")
            for row in cur.fetchall():
                print(row)

except (Exception, psycopg2.DatabaseError) as error:
    print(error)


finally:
    if conn is not None:
        conn.close()
    print('PostgreSQL connection is closed')
    print('table post_users_test import completed')


# Checking the data from PostgreSQL      
cur.execute("SELECT * FROM post_users_test")     
for row in cur.fetchall():         
    print(row)
```

Tutorial: cargando datos a PostgreSQL con archivos CSV

```python
pip install psycopg2

# Script
import psycopg2
conn = psycopg2.connect("host=localhost dbname=postgres user=postgres")
cur = conn.cursor()

cur.execute("""
    CREATE TABLE users(
    id integer PRIMARY KEY,
    email text,
    name text,
    address text
)
""")
conn.commit()

insert_query = "INSERT INTO users VALUES {}".format("(10, 'hello@dataquest.io', 'Some Name', '123 Fake St.')")
cur.execute(insert_query)
conn.commit()

cur.execute("INSERT INTO users VALUES (%s, %s, %s, %s)", (10, 'hello@dataquest.io', 'Some Name', '123 Fake St.'))
conn.commit()

with open('user_accounts.csv', 'r') as f:
    reader = csv.reader(f)
    next(reader) # Skip the header row.
    for row in reader:
        cur.execute(
        "INSERT INTO users VALUES (%s, %s, %s, %s)",
        row
    )
conn.commit()

with open('user_accounts.csv', 'r') as f:
    # Notice that we don't need the `csv` module.
    next(f) # Skip the header row.
    cur.copy_from(f, 'users', sep=',')
conn.commit()

cur.execute('SELECT * FROM notes')
one = cur.fetchone()
all = cur.fetchall()
```

Enlaces de interés
- [pgcopydb][1]: herramienta para automatizar la copia de datos de una base de datos a otra.
- [Usando COPY TO y COPY FROM con psycopg3][2]

[1]:	https://github.com/dimitri/pgcopydb
[2]:	https://www.psycopg.org/psycopg3/docs/basic/copy.html