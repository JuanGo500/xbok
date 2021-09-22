# Import from csv
```python
with open('/Users/Juan/Downloads/Movimientos.csv') as csvfile:
    datos=csv.reader(csvfile,delimiter=',')
    for row in datos:
        print(','.join(row))
```
# Import directly to pandas
```python
import pandas as pd

df = pd.read_csv (r'Path where the CSV file is stored\File name.csv')
print (df)
```
