# Obtener el número de productos que tiene ventas superiores a 0

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