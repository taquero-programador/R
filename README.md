# R

## Primeros pasos
```r
(1:40) ^ 2
```
Esto produce los números del 1 al 40 elevados al cuadrado. Cada línea viene precedida pro el ordinal
del primer valor de la línea en el conjunto de datos de salida. Por ejemplo, si una línea comienza
con `[14]` eso indica que el primer valor en esa línea ocupa el puesto 14 de los valores que aparecen
en la salida.

## Ayuda
Se puede pedir ayuda sobre cualquier función, paquete, instrucción, conjunto de datos, etc. Para
ellos hay que usar la función `help()`:
```r
help("mean")
```
También puede usar `?var`.

La ayuda sobre funciones incluye descripciones de sus parámetros de entrada y valor de retorno.
La última parte de la ayuda es muy interesante, pues incluye ejemplos de uso de la función.
```r
example(seq)
# para obtener información más detallada
help("seq")
```

## Vignettes
Los paquetes de R están obligados a incluir documentación sobre sus funciones y conjuntos de datos.
Sin embargo, a veces es dificil entender la utilidad de un paquete...

## Variables
Ejemplos de cómo declarar variables:
```r
x <- 5
2 * x + 3
```
Crear una variable que almacene la palabra `Mujico`:
```r
pais <- "Mujico"
nchar(pais) # retorna el número de letras en la variable
pais # retorna el valor de la variable
```

## Vectores
Los vectores son arreglos ordenados en los cuakes se pueden almacenar información numérico
(variable cuantitativa), alfanumérico (variable cualitativa) o lógico (`TRUE` o `FALSE`), pero no
mezclas de estos. La función en R para crear una vector es `c()` y que significa concatenar; dentro
de los paréntesis de esta función se ubica la información a almacenar. Ejemplo:
```r
edad <- c(15, 19, 13, NA, 20)
deporte <- c(TRUE, TRUE, NA; FALSE, TRUE)
comic_fav <- c(NA, 'Superman', 'Batman', NA, 'Batman')
```
- `NA` es `Not Avaliable`
- `edad` es un vector cuantitativo
- `deporte` es un vector lógico
- `comic_fav` es un vector cualitativa

> Se puede utilizar comillas simples o dobles para ingresar valores de una variable cualitativa

#### Extraer valores de un vector
Se utilizan los corchetes `[]` y dentro de ellos la posición o posiciones de interes.

Por ejemplo, para extrar la edad de la tercera persona:
```r
edad[3]
```
Para obtener las posiciones 2 y 5 de `comic_fav`:
```r
comic_fav[c(2, 5)]
```
Obtener todos los valores de `deporte`, excepto la posición 4:
```r
deporte[-4]
```

## Matrices
Las matrices son arreglos rectangulares de filas y columnas con información numérica, alfanumérica
o lógica. Para construir una matriz se usa la función `matrix()`. Por ejemplo, para crear una matriz
de 4 filas y 5 columnas (de dimensiones 4 x 5) con los primero 20 números positivos:
```r
mimatriz = matrix(data=1:20, nrow=3, ncol=5, byrow=FALSE)
```
**`data`**: sirve para indicar los datos que se van a almacenar en la matriz.

**`nrow (fila), ncol (columna)`**: definen la dimensión de la matriz.

**`byrow`**: indica si la información en `data` se debe ingresar en filas o no.

#### Extrar elementos de una matriz
Para acceder a los elementos dentro de una matriz se usan los corchetes `[]` y, dentro, separado por
coma, el número de filas y columnas de interes.

Por ejemplo, para acceder al valor de la fila 3 y la columna 4:
```r
mimatriz[3, 4]
```
Para recuperar toda la fila 2:
```r
mimatriz[2, ]
```
Para recuperar toda la columna 5:
```r
mimatriz[, 5]
```
Para recuperar la matriz sin las columnas 2 y 4:
```r
mimatriz[, -c(2, 4)]
```
Recuperar la matriz sin la fila 1 y la columna 3:
```r
mimatriz[-1, -3]
```

## Arreglos
Un arreglo es un matriz de varias dimensiones con información numérica, alfanumérica o lógica. Para
construir un arreglo se usa la función `array()`. Por ejemplo, para crear un arreglo de 3 x 4 x 2
con las primeras 24 letras en minúsculas del alfabeto:
```r
miarray <- array(data=letters[1:24], dim=c(3, 4, 2))
```
**`dim(filas. columnas, dimensiones)`**: permite definir las dimensiones en el arreglo.

#### Extraer elementos de un arreglo
Se utilizan los corchetes y, dentro, las coordenadas del objeto.

Por ejemplo, acceder al valor de la fila 1, columna 3 y dimensión 2:
```r
miarray[1, 3, 2]
```
Para extrar la segunda dimensión completa:
```r
miarray[, , 2]
```
Extrer la tercera columna de todas las dimensiones:
```r
miarray[, 3, ]
```

## Marco de datos
El marco de datos o *data frame* es uno de los objetos más utilizados porque permite agrupar vectores
con información de diferente tipo (numérica, alfanumérica o lógica) en un mismo objeto, la única
restricción es que los vectores deben tener la misma longitud. Para crear un marco de datos se usa
la función `data.frame()`.

Por ejemplo, crear un marco de datos con los vectores `edad`, `deporte` y `comic_fav` definidos anteriormente.
```r
mi_marco <- data.frame(edad, deporte, comic_fav)
```

#### Extraer elementos de un marco de datos (*data frame*)
Para recuperar la columnas en un *data frame* se puede usar el operador `$` (frame$col_name [vector]),
corchetes simples `[]` (frame[int] [columna]) o corchetes dobles `[[]]` (frame[["col_name"]] [vector]).

Por ejemplo, para extrar la columna `deporte` del *data frame* `mi_marco` como un vector:
```r
mi_marco$deporte
```
Otra manera de obtener los datos de `deporte` es indicar el número de columna:
```r
mi_marco[,2] # retorna una fila
mi_marco[2] # retorna una columna
```
Usar el nombre de la columna y doble corchete para acceder a los valores:
```r
mi_marco[["deporte"]] # retorna una fila
mi_marco["deporte"] # retorna una columna
```
Para extrar las columnas `deporte` y `edad`:
```r
mi_marco[c("deporte", "edad")]
# or
mi_marco[c(2,1)]
```
Para obtener las posiciones de 2 hasta la 4 de la columna `edad`:
```r
mi_marco[2:4, 1]
```

#### Extraer subconjuntos de un marco de datos
