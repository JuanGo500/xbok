# Pandas
Al usar [] en una expresión, el resultado es un dataframe.

## Cargar datos

```python
ubicacion="/Users/Juan/Dropbox/XND/Data/Apple_Sales.csv"
datos=pd.read_csv(ubicacion)
```

## Crear un dataset
1. Para crear un dataset se incluyen listas de valores para cada atributo.

```python
import pandas as pd

miDataset= {
    "coche":["seat","citroen"],
    "moto":["kawasaki","vespa"],
    "persona":["juan","luis","pepe"]
}

ds=pd.DataFrame(miDataset)

print(ds)
```
2. También se puede incluir una lista de listas de valores, una lista de índices y una lista de columnas

```python
df = pd.DataFrame([[1, 2], [4, 5], [7, 8]], index=["cobra", "viper", "sidewinder"],columns=["max_speed", "shield"])
print(df)
```

## Localizar datos
- Por número de índice: `df.iloc[[1]]`
- Varias filas: `df.iloc[[0,2]]` 
- Por nombre de índice: print(df.loc[["day1"]])

```
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

print(df) 
```

## Main functions
- Describir los datos: `df.describe()`
- Primeras filas: `df.head()`
- Selecting and filtering data: `df[df['column_name'] == value]` 
- Applying aggregate functions: `df.groupby('column_name').agg({'other_column':'sum'})`
- Sorting and grouping data: `df.sort_values(by=['column_name'])`
- Merging and joining datasets: `df1.merge(df2, on='column_name', how='inner')`
- Manipulating data with Python-specific code: `df['new_column'] = df['column_name'].apply(lambda x: x)`

## Transformation

- Find duplicates: `df.duplicated()`
- Remove rows: `df = df.drop(df.index[[0, 1]])`
- Remove columns: `df = df.drop('edad', axis=1)`
  
