# python-research-table-merge

## Trabajar con datos usando pandas

> ¿Como mezclar datos de forma vertical entre dos tablas? Técnicas usando estrategias de join y merge

Pandas DataFrame es una estructura de 2 dimensiones de tamaño mutable. Permite almacenar datos de forma tabular usando etiquetas basadas en filas y columnas.

Se puede hacer uso diferentes métodos como join, merge y concat, que nos ayudan a unir diferentes estructuras de datos `data frames`

### Usando `.concat()`

Esta función concatena dos `data frames` y devuelve uno nuevo.

```python
# importing pandas module
import pandas as pd 

# Define a dictionary containing employee data 
data1 = {
	'Name':['Jai', 'Princi', 'Gaurav', 'Anuj'], 
	'Age':[27, 24, 22, 32], 
	'Address':['Nagpur', 'Kanpur', 'Allahabad', 'Kannuaj'], 
	'Qualification':['Msc', 'MA', 'MCA', 'Phd']
} 

# Define a dictionary containing employee data 
data2 = {
	'Name':['Abhi', 'Ayushi', 'Dhiraj', 'Hitesh'], 
	'Age':[17, 14, 12, 52], 
	'Address':['Nagpur', 'Kanpur', 'Allahabad', 'Kannuaj'], 
	'Qualification':['Btech', 'B.A', 'Bcom', 'B.hons']
} 

# Convert the dictionary into DataFrame  
df = pd.DataFrame(data1,index=[0, 1, 2, 3])

# Convert the dictionary into DataFrame  
df1 = pd.DataFrame(data2, index=[4, 5, 6, 7])

print(df, "\n\n", df1) 

# using a .concat() method
frames = [df, df1]
result_concat = pd.concat(frames)

print(result_concat)
```

### Concatenar con `inner join`

Concatena los datos tomando la intersección de datos entre los dos `data frames` y devuelve una nueva estructura de datos.

```python
# applying concat with axes join = 'inner'
result_inner = pd.concat([df, df1], axis=1, join='inner')

print(result_inner)
```

### Concatenar con `outer join`

Concatena tomando todos los datos de los dos `data frames` y generando una nueva estructura de datos con toda la información.

```python
# using a .concat for union of dataframe, join = 'outer'

result_outer = pd.concat([df, df1], axis=1, sort=False)

print(result_outer)
```

### Concatenar usando `join_axes`

Resulta en la union de las dos estructuras.

```python
# using join_axes

result_join_axes = pd.concat([df, df1], axis=1, join_axes=[df.index])

print(result_join_axes)
```

### Concatenar usando `.append()`

Esta función concatena a lo largo del indice 0.

```python
# using append function

result_append = df.append(df1)

print(result_append)
```


### Concatenar ignorando los indices

Mezcla la información ignorando el indice de las estructuras.

```python
# using ignore_index

result_ignore_index = pd.concat([df, df1], ignore_index=True)

print(result_ignore_index)
```

### Concatenar usando claves de grupo

Crea nuevos grupos para los datos.

```python
# using keys 

frames = [df, df1]

result_using_keys = pd.concat(frames, keys=['x', 'y'])

print(result_using_keys)
```

### Concatenar con datos mixtos

Mezclar series y data frames usando el indice de los datos.

```python
# creating a series

s1 = pd.Series([1000, 2000, 3000, 4000], name='Salary')

print(df, "\n\n", s1) 

# combining series and dataframe

result_combining = pd.concat([df, s1], axis=1)

print(result_combining)
```

### Uniendo datos con `.merge()`

```python
# using .merge() function

result_merge = pd.merge(df, df1, on='key')

print(result_merge)
```

### Unir tablas usando sus columnas como indices

```python
# merging dataframe using multiple keys

result_mutiple_keys = pd.merge(df, df1, on=['key', 'key1'])

print(result_mutiple_keys)
```

### Union de tablas a la izquierda

```python
# using keys from left frame

result_left = pd.merge(df, df1, how='left', on=['key', 'key1'])

print(result_left)
```

### Union de tablas a la derecha

```python
# using keys from right frame

result_right = pd.merge(df, df1, how='right', on=['key', 'key1'])

print(result_right)
```

### Unir tablas con todos los datos de ambas tablas usando `outer`

```python
# getting union  of keys

result_outer_on_keys = pd.merge(df, df1, how='outer', on=['key', 'key1'])

print(result_outer_on_keys)
```

### Unir tablas solo con la intersección de datos entre ambas `inner`

```python
# getting intersection of keys

result_inner_on_keys = pd.merge(df, df1, how='inner', on=['key', 'key1'])

print(result_inner_on_keys)
```

### Usar `.join()` para combinar las columnas de las dos tablas

```python
# joining dataframe

result_join = df.join(df1)

print(result_join)
```

### Union con `.join()` usando la estrategia `outer`

```python
# getting union

result_join_outer = df.join(df1, how='outer')

print(result_join_outer)
```

### Union con `.join()` usando una columna como llave

```python
# using on argument in join

result_join_on_column = df.join(df1, on='Key')

print(result_join_on_column)
```

### Multi indexado de datos

```python
df = pd.DataFrame(data1, index=pd.Index(['K0', 'K1', 'K2'], name='key'))

index = pd.MultiIndex.from_tuples([
	('K0', 'Y0'), ('K1', 'Y1'),
	('K2', 'Y2'), ('K2', 'Y3')],
	names=['key', 'Y'])

# Convert the dictionary into DataFrame  

df1 = pd.DataFrame(data2, index= index)

print(df, "\n\n", df1)

# joining singly indexed with multi indexed

result_multi_indexed = df.join(df1, how='inner')

print(result_multi_indexed)
```
