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
typeof(obj) # retorna el tipo de dato del objeto
class(obj) # retorna el tipo (array, matrix, dataframe, etc.)
attributes(obj) # retorna los nombres de columnas, clase y nombre de filas
names(obj) # retorna el nombre de las columnas del objeto
```

## Vignettes
Los paquetes de R están obligados a incluir documentación sobre sus funciones y conjuntos de datos.
Sin embargo, a veces es difícil entender la utilidad de un paquete...

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

## Tipos de datos
En R los datos pueden ser de diferentes tipos. Cada tipo tiene características particulares
que lo distinguen de los demás. Entre otras cosas, algunas operaciones solo se pueden
realizar con tipos de datos específicos.

#### Datos más comunes
Los tipos de datos más común en R son los siguientes:
Tipo | Ejemplo | Nombre en inglés
-|-|-
Entero | `1` | integer
Numérico | `1.3` | numeric
Cadena de texto | `"uno"` | character
Factor | `uno` | factor
Lógico | `TRUE` | logical
Perdido | `NA` | NA
Vacío | `NULL` | null

Además de estos tipos, R también cuenta con datos numéricos complejos (con una parte real y
una imaginaria), `raw` (bytes), fechas y raster, etc. Estos tipos tienen aplicaciones muy específicas,
por ejemplo, los datos de tipo fechas son ampliamente usados en economía para analísis de series de tiempo.

#### Entero y numérico
Como su nombre lo indica, los datos enteros representan números enteros, sin una parte decimal o fraccionaria.

Los datos numéricos representan números, a diferencia de los datos enteros es que tienen
una parte decimal o fraccionaria.

Los datos numéricos también son llamados *float* (flotante).

#### Factor
un factor es un tipo de datos específico de R. Puede ser descrito como un dato numérico
representado por una etiqueta.

Supongamos que tenemos un conjunto de datos que representa el sexo de personas encuestadas
por teléfono, pero estos se encuentran capturados por los números `1` y `2`. El 1 corresponde a **femenino** y el 2 a **masculino**.

Podemos indicar en consola y para otros analísis, que muestre los 1 como `femenino` y los 2 como `masculinos`.

Por último, cada una de las etiquetas o valores que pueden asumir un factor se conococen como **nivel**.
En el caso de `femenino` y `masculino`, serían dos niveles.

#### Lógico
Los datos de tipo lógico solo tiene dos valores posibles: `TRUE` (verdadero) y `FALSE` (falso).

#### `NA` y `NULL`
En R, usamos `NA` para representar datos perdidos, mientras que `NULL` representa la ausencia de datos.

La diferencia entre las dos es que, un dato `NULL` aparece solo cuando R intents recuperar un dato
y no encuentra nada, mientras que `NA` es usado para representar explícitamente datos perdidos,
omitidos o que por alguna razón son faltantes.

## Coerción
En R los datos pueden ser cuercionados, es decir, forzados para ser transformados de un tipo a otro.

La coerción es muy importante. Cuando pedimos a R relizar alguna operación, intentará coercionar
de manera implícita, sin avisarnos, los datos de su tipo original al tipo correcto que permita relizarla.
Habra ocasiones en las que R tenga éxito y la operación ocurra sin problemas, y otras en
las que falle y obtengamos un error.

La coerción de tipos se reliza de los datos más restrictivos a los más flexibles.

Las coerciones ocurren en el siguiente orden:

'''r
lógico -> entero -> numérico -> cadena de texto
'''

#### Coerción explícita con `as()`

Función | Tipo al que hace coerción
-|-

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
El marco de datos o *dataframe* es uno de los objetos más utilizados porque permite agrupar vectores
con información de diferente tipo (numérica, alfanumérica o lógica) en un mismo objeto, la única
restricción es que los vectores deben tener la misma longitud. Para crear un marco de datos se usa
la función `data.frame()`.

Por ejemplo, crear un marco de datos con los vectores `edad`, `deporte` y `comic_fav` definidos anteriormente.
```r
mi_marco <- data.frame(edad, deporte, comic_fav)
```

#### Extraer elementos de un marco de datos (*dataframe*)
Para recuperar la columnas en un *dataframe* se puede usar el operador `$` (frame$col_name [vector]),
corchetes simples `[]` (frame[int] [columna]) o corchetes dobles `[[]]` (frame[["col_name"]] [vector]).

Por ejemplo, para extrar la columna `deporte` del *dataframe* `mi_marco` como un vector:
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
Para extraer partes de un marco de datos se puede usar la función `subset(x, subset, select)`. El
parámetro `x` sirve para indicar el marco de datos, `subset` permite indicar una condición y
`select` permite filtar las columnas.

Acceder a todos los registros dentro del *dataframe* solo si `deporte` es `TRUE`:
```r
subset(mi_marco, subset=deporte == TRUE)
```
Obtener los valores cuando `edad` sea mayor o igual a `17`:
```r
subset(mi_marco, subset=edad >= 17)
```
Obtener la columna `deporte` y `comic_fav` de las personas menores `20`:
```r
subset(mi_marco, subset=edad <20, select=c('deporte', 'comic_fav'))
```
Obtener todos los datos de `mi_marco` con las personas menores de `20` y que es `TRUE` en `deporte`:
```r
subset(mi_marco, subset=edad < 20 & deporte == TRUE)
```
#### Leer una base de datos (url)
De esta base extraer un subconjunto que contenga `edad`, `peso`, `altura` y `sexo`, de aquellos que
midan más de 185 cm y con un peso mayor a 80 kg.
```r
url <- 'https://raw.githubusercontent.com/fhernanb/datos/master/medidas_cuerpo'
dt1 <- read.table(url, header=TRUE)
dim(dt1) # retorna la dimensión de la base [1] 36 (filas) 6 (columnas)

dt2 <- subset(x=dt1, subset=altura > 185 & peso > 80, select=c('sexo', 'edad', 'peso', 'altura'))
dt2 # retorna el nuevo subconjunto
```

## Listas
Las listas son otro tipo de objeto muy usado para almacenar objetos de diferente tipo. La sintaxis
para crear una lista es `list()`.

Para crear una lista que contenga tres objetos: un vector con 5 números de nombre `mi_vector`, una
matriz de dimensiión 6x4 de 12 números positivos llamada `mi_matriz2` y el *dataframe* `mi_marco`.
```r
set.seed(12345)
mi_vector <- runif(n=5)
mi_matriz2 <- matrix(data=1:12, ncol=6)
mi_lista <- list(E1=mi_vector, E2=mi_matriz2, E3=mi_marco)
```
La función `set.seed()` permite fijar la semilla de tal manera que los números aleateorios generados
por la segunda línea en `runif()` sean siempre los mismos. Para la creación de la lista se pasan `E1`, `E2` y `E3` como argumentos y nombres especiales para cada uno de los elementos.

#### Extraer elementos de una lista
Para recuperar elementos de una lista se puede usar `$`, `[]` o `[[]]`.

Para acceder a la matriz almanecada con el nombre de `E2` dentro del objeto `mi_lista`:
```r
mi_lista$E2
mi_lista[[2]] # indicar la posición del objeto en lugar del nombre
```
Usemos `class()` para ver la diferencia entre estos dos objetos:
```r
class(mi_lista$E2) # "matrix" "array"
class(mi_lista[[2]]) # "matrix" "array"
class(mi_lista[2]) # "list"
```
> Al manipular una lista con `$` y `[[]]` se obtienen los objetos almacenados, con `[]` se obtiene una lista.

```r
# vector con las primera 20 letras en mayúsculas
v1 <- c(LETTERS[1:20])
# matriz de 10x10 con 100 números positivos
m1 <- matrix(data=1:100, rcol=10, ncol=10)
# matriz de identidad de 3x3
mi1 <- matrix(data=diag(3), 3,3) # or diag(3)
# lista con los 3 objetos anteriores
l1 <- list(a=v1, b=m1, c=mi1)
# crear un dataframe con 3 vectores (edad, música y relación)
edad <- c(29, 39, 30)
music <- c('rock', 'romantica', 'varios')
rel_stable <- c(TRUE, FALSE, TRUE)
df1 <- data.frame(edad, music, rel_stable)
# ¿Cuál es el error?
matrix(edad, deporte, comic_fav)
# solución
matrix(data=c(edad, deporte, comic_fav), 3,5)
# o crear un dataframe
data.frame(edad, deporte, comic_fav)
```

## Guía de estilo

#### Nombres de los archivos
Se suguiere que el nombre usado para nombrar los archivos tenga sentido y que termine con la
extensión `.R`.

#### Nombre de los objetos
Se recomienda usar `_` dentro de los nombre de objetos. Puede comensar por una letra o punto. Si
comienza por punto, el siguiente carácter no puede ser un número.

...

## Usando la consola
La función `readline` sirve para escribir un mensaje en la consola y solicitar al usuario una
información que luego se pueda utilizar para realizar alguna operación.

```r
my_name <- readline(prompt="Ingrese su nombre: ")
my_age <- readline(promt="Ingrese su edad: ")
my_age <- as.integer(my_age) # convierte el carácter a entero
# or
my_age <- as.integer(readline(prompt="Ingrese su edad: "))
print(paste("Hola,", my_name,
    "el año siguiente tendras",
    my_age + 1,
    "años de edad."))
```

#### Usando ventanas emergentes con `svDialogs`
El paquete `svDialogs` se puede usar para crear ventanas emergentes con un mensaje y solicitar
información.

Este ejemplo hace lo mismo que el anterior, pero lanza una ventana emergentes usando `svDialogs`:
```r
install.packages("svDialogs") # instala el paquete
library(svDialogs) # para usar el paquete

my_name <- dlgInput(message="Ingrese su nombre: ")$res
my_age <- dlgInput(message="Ingrese su edad: ")$res
my_age <- as.integer(my_age)
print(paste("Hola,", my_name,
    "el año siguiente tendras",
    my_age + 1,
    "años de edad."))
```

#### Botones para responder
La función `winDialog` del paquete *utils* sirve para crear botones de diálogo (solo en Windows).
```r
library(utils)

winDialog(type="ok", message="¿Ve el mensaje?")
winDialog(type="okcancel", message="Dos opciones") # muestra dos botones
winDialog(type="yesno", message="Dos opciones")
winDialog(type="yesnocancel", message="Tres opciones") # muestra tres botones

# usar condición, ejemplo:
answer <- winDialog(type="yesno", mess="Elige una opción")
if(answer) {
    print('Excelente!')
}
else {
    print('Lastima')
}
```
