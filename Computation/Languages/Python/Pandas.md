# Pandas

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
- Por número de índice: print(ds.iloc[[1]])
- Por nombre de índice: print(ds.loc[["cobra"]])


## Main functions
- Reading data into a dataframe: `df = pd.read_csv('example.csv').`
- Selecting and filtering data: `df[df['column_name'] == value]` 
- Applying aggregate functions: `df.groupby('column_name').agg({'other_column':'sum'})`
- Sorting and grouping data: `df.sort_values(by=['column_name'])`
- Merging and joining datasets: `df1.merge(df2, on='column_name', how='inner')`
- Manipulating data with Python-specific code: `df['new_column'] = df['column_name'].apply(lambda x: x`
  