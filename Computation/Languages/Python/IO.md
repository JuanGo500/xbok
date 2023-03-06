# IO

## Import from csv
```python
with open('/Users/Juan/Downloads/Movimientos.csv') as csvfile:
    datos=csv.reader(csvfile,delimiter=',')
    for row in datos:
        print(','.join(row))
```

## Export to json
```python
import json

data=['a','b']

with open('filename.json','w') as f:
    json.dump(data,f)
    
```
