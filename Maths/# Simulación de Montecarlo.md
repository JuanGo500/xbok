# Simulación de Montecarlo

```R
# Creamos la urna
bolas=rep(c("rojo","azul","blanco"),c(7,2,1))

# Comprobamos el número de bolas 
bolas

# Cogemos una bola aleatoria
sample(bolas,1)

# Repetimos la extracción muchas veces
events=replicate(100000,sample(bolas,1))

# Tabulamos el resultado
resultados=table(events)
resultados

# Mostramos las frecuencias relativas
prop.table(resultados)

```

