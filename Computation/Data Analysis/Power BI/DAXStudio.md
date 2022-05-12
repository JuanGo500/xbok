# Syntax
- DEFINE MEASURE measure=expression
- EVALUATE {expression}

## Examples
- Evaluate a measure existing in the model: EVALUATE{[Measure]}
- Evaluate an expression: EVALUATE{SUM(Table[Column])}


# Procedures
## Review DAX from a visual
- PBID>View>Performance Analyzer>Export
- DAXS>Load Perf Data>Double click on result

## Export data from table
Advanced>Export data

# DMV
Dynamic Management Views
– Getting all your measures with: $SYSTEM.TMSCHEMA_MEASURES
– Determining the measure dependency: $SYSTEM.DISCOVER_CALC_DEPENDENCY
– Get all the tables: $SYSTEM.DBSCHEMA_TABLES
– Get all the columns: $SYSTEM.DBSCHEMA_COLUMNS

# Examples
## Obtener el número de productos que tiene ventas superiores a 0

```DAX
DEFINE
    MEASURE Sales[Transacc] =
        COUNTROWS ( Sales )
EVALUATE
{
    COUNTROWS (
        ADDCOLUMNS (
            FILTER ( VALUES ( 'Product'[Product Name] ), [Transacc] > 0 ),
            "TR", [Transacc]
        )
    )
}
```