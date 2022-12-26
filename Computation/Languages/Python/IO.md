# Import from csv
```python
with open('/Users/Juan/Downloads/Movimientos.csv') as csvfile:
    datos=csv.reader(csvfile,delimiter=',')
    for row in datos:
        print(','.join(row))

