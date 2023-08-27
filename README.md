# R

## Primeros pasos
```r
(1:40) ^ 2
```
Esto produce los números del 1 al 40 elevados al cuadrado. Cada línea viene precedida por el ordinal
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
En R, los datos pueden ser de diferentes tipos. Cada tipo tiene características particulares
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

Podemos indicar en consola y para otros analísis, que muestre los 1 como `femenino` y los 2 como `masculino`.

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
En R, los datos pueden ser cuercionados, es decir, forzados para ser transformados de un tipo a otro.

La coerción es muy importante. Cuando pedimos a R relizar alguna operación, intentará coercionar
de manera implícita, sin avisarnos, los datos de su tipo original al tipo correcto que permita relizarla.
Habra ocasiones en las que R tenga éxito y la operación ocurra sin problemas, y otras en
las que falle y obtengamos un error.

La coerción de tipos se reliza de los datos más restrictivos a los más flexibles.

Las coerciones ocurren en el siguiente orden:
```r
lógico -> entero -> numérico -> cadena de texto
```

#### Coerción explícita con `as()`

Función | Tipo al que hace coerción
-|-
`as.integer()` | Entero
`as.numeric()` | Numérico
`as.character()` | Cadena de texto
`as.factor()` | Factor
`as.logical()` | Lógico
`as.null()` | `NULL`

Todas estas funciones aceptan como argumento datos o vectores.

## Verificar el tipo de un dato
Se puede usar la función `class()`.

#### Verificar con la función `is()`

Función | Tipo que verifica
-|-
`is.integer()` | Entero
`is.numeric()` | Numérico
`is.character()` | Cadena de texto
`is.factor()` | Factor
`is.logical()` | Lógico
`is.na()` | `NA`
`is.null()` | `NULL`

Estas funciones toman como argumento un dato.

## Operadores
Los operadores son los símbolos que le indican a R que tarea relizar.

Existen operadores específicos para cada tipo de tarea. Los operadores principales son:
- Aritméticos
- Relacionales
- Lógicos
- De asignación

#### Operadores aritméticos
En R, tenemos los siguientes operadores aritméticos:

Operador | Operación | Ejemplo | Resultado
-|-|-|-
`+` | Suma | `5 + 3` | 8
`-` | Resta | `5 - 3` | 2
`*` | Multiplicación | `5 * 3` | 15
`/` | División | `5 / 3` | 1.666667
`^` | Potencia | `5 ^ 3` | 125
`%%` | División entera | `5 %% 3` | 2

Es posible realizas operaciones aritméticas con datos de tipo entero y numérico.

#### Operadores relacionales
Los operadores relacionales son usados para hacer comparaciones y devuelve `TRUE` o `FALSE`.

Operador | Comparación | Ejemplo | resultado
-|-|-|-
`<` | Menor que | `5 < 3` | `FALSE`
`<=` | Menor o igual que | `5 <= 3` | `FALSE`
`>` | Mayor que | `5 > 3` | `TRUE`
`>=` | Mayor o igual que | `5 >= 3` | `TRUE`
`==` | Exactamente igual que | `5 == 3` | `FALSE`
`!=` | No es igual que | `5 != 3` | `TRUE`

Es posible comparar cualquier tipo de dato sin que resulte en error.

Sin embargo, al usar los operadores `>`, `>=`, `<` y `<=` con cadenas de texto, estos tienen un comportamiento especial.

```r
"casa" > "barco" # TRUE
```
La comparación se realiza en orden alfabético, por lo que "c" está antes de que "b".

#### Operadores lógicos
Los operadores lógicos son usados para operaciones de álgebra Booleana, es decir, para
describir relaciones lógicas expresadas como `TRUE` o `FALSE`.

Operador | Comparación | Ejemplo
-|-|-
`x \| y` | x o y es verdadero | `TRUE \| FALSE`
`x & y` | x Y y son verdaderos | `TRUE & FALSE`
`!x` | x no es verdadero (negación) | `!TRUE`
`isTRUE(x)` | x es verdadero (afirmación) | `isTRUE(TRUE)`

Los operadores `|` y `&` siguen estas reglas:
- `|` devuelve `TRUE` si algunos de los datos es verdadero
- `&` devuelve `TRUE` si ambos datos son verdaderos
- `|` solo devuelve `FALSE` si ambos datos son falsos
- `&` devuelve `FALSE` si alguno de los datos es falso

Estos operadores pueden ser usados con datos del tipo numérico, lógico y complejo.

#### Orden de operaciones

Orden | Operadores
-|-
1 | `^`
2 | `*` `/`
3 | `+` `-`
4 | `<` `>` `<=` `>=` `==` `!=`
5 | `!`
6 | `&`
7 | `\|`
8 | `<-`

Si deseamos que una operación ocurra antes que otra, rompiendo el orden, usamos paréntesis.

## Estructura de datos
Las estructuras de datos son objetos que contienen datos.

Tabla con las principales estructuras de control en R.

Dimensiones | Homogeneas | Heterogeneas
-|-|-
1 | Vector | Lista
2 | Matriz | Data Frame
3 | array |

## Vectores
Los vectores son arreglos ordenados en los cuakes se pueden almacenar información numérico
(variable cuantitativa), alfanumérico (variable cualitativa) o lógico (`TRUE` o `FALSE`), pero no
mezclas de estos. La función en R para crear una vector es `c()` y que significa concatenar; dentro
de los paréntesis de esta función se ubica la información a almacenar. Ejemplo:

Verificar que el `3` es un vector:
```r
is.vector(3) # TRUE
```
Usar la función `length()` para conocer el largo de un vector:
```r
length(3)
```

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

#### Vectorización de vectores
Existen unas operaciones que se aplican a cada uno de los elementos. A este proceso
se le conoce como **vectorización**.

Las operaciones aritméticas y relacionales puden vectorizarse. Si la aplicamos a un vector,
la operación se relizará em cada uno de los elementos contenidos.

Por ejemplo, creamos un vector:
```r
vector <- c(2, 3, 6, 7, 8, 10, 11)
```
Al aplicar la operación aritmética, el resultado se aplica a cada elemento:
```r
vector + 2
```
Al aplicar operaciones relacionales, obtenemos un vector de `TRUE` y `FALSE`:
```r
vector > 7
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

**`cbind()`**: une vectores usando cada uno como columnas.

**`rbind()`**: une vectores usando cada uno como filas.
```r
# usar cada vector como filas
matriz <- rbind(vector1, vector2, vector3)
# usar cada vector como columna
matriz <- cbind(vector1, vector2, vector3)
```

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
La vectorización también se aplica a las matrices.

La función `t()` permite transponer una matriz, es decir, rotatrla 90°.
```r
# matriz de 3 x 
matriz <- matrix(1:6, nrow=3)
# transponer
matriz_t <- t(matriz)
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
# crear un dataframe manual
df1 <- data.frame(
    "entero" = 1:4,
    "factor" = c(letters[1:4]),
    "numero" = c(1.2, 3.4, 4.5, 5.6),
    "cadena" = as.character(c(letters[1:4]))
# coercionar una matriz
matriz <- matrix(1:24, ncol=4)
df <- as.data.frame(matriz)
class(df)
```
Un dataframe también se puede vectorizar.

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
# or
mi_marco[c(1,2), c("edad")]
```

#### Extraer subconjuntos de un marco de datos
Para extraer partes de un marco de datos se puede usar la función `subset(x, subset, select)`. El
parámetro `x` sirve para indicar el marco de datos, `subset` permite indicar una condición y
`select` permite filtar las columnas.

Acceder a todos los registros dentro del *dataframe* solo si `deporte` es `TRUE`:
```r
subset(mi_marco, subset=deporte == TRUE)
# similar a
mi_marco[mi_marco$deporte == TRUE]
# colocar una coma al final retorna las columnas
mi_marco[mi_marco$deporte == TRUE, ]
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
mi_lista$E2[1,] # fila 2 y todas las columnas [fila, columna] or [1:3,]
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

## Coerción en estructuras de datos
También se puede usar la función `as()` en las estructuras de datos:

Función | Coerciona a | Coerciona exitosamente 
-|-|-
`as.vector()` | Vector | Matriz
`as.matrix()` | Matriz | Vectores, Data frames
`as.data.frame()` | Data frame | Vectores, Matrices
`as.list()` | Lista | Vectores, Matrices, Data frames

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

## Funciones en R
La instalación base de R tiene suficientes funciones para que relicemos todas las tareas básicas
de análisis de datos, etc.

Sin embargo, es común que necesitemos realizar tareas para las que no existe una función
específica.

#### ¿Por qué necesitamos nuestras porpias funciones?
Supongamos que tenemos un jefe que no ha pedido un histograma con datos de edad que hemos recogido
en un encuestas.

Esto es sencillo de resolver con la función `hist()`. Solo tenemos que pasar un vector numérico como
argumento para generar una gráfica.

Primero, generaremos datos aleateorios de una distribució normal con la función `rnomr()`. Esta
función tiene los siguientes argumentos:
- `n`: cantidad de números a generar
- `mean` media de la distribución de la que sacaremos los números
- `sd`: desviación estándar de la distribución para sacar los números

Además, llamaremos a `set.seed()` para que estos resultados sean replicantes. Cada que llamamos a
`rnomr()` se generar números aleateorios diferentes, pero si antes llamamos a `set.seed()` con un
número específico como argumento obtendremos los mismos resultados.
```r
# obtener 1500 números con media 15 y desviación estándar de .75
set.seed(173)
edades <- rnomr(n=1500, mean=15, sd=.75)
# ver los primeros 10 números del objeto
edades[1:10]
# generar la gráfica
hist(x=edades)
```
Podemos calcular la media de los datos con la función `mean()`, la desviación estándar con `sd()`, y
podemos agregar los resultados de este calculo al histograma usando `abline()`.
```r
# calcular la media y desviación
media <- mean(edades)
des_est <- sd(edades)
# rojo para la media y azúl para la desviación
hist(edades, main="Edades", xlab="Datos", ylba="Frecuencia", col="gold")
abline(v=media, col="red")
abline(v=media + (des_est *c(1, -1)), col="blue")
```

#### Funciones definidas por el usuario
Una función tiene nombre, argumentos y un cuerpo. Las funciones definidas por el usuario tiene
la siguiente estructura:
```r
nombre <- function(argumentos) {
    operaciones
}
```
Los argumentos pueden ser datos, estrucutras de datos, conexiones a archivos u otras funciones y
deben tener nombres diferentes.

#### Nuestra primera función
Función para calcular el área de un cuadrilátero: `lado x lado`.

```r
area_cuad <- function(lado1, lado2) {
    lado1 * lado2
}
# llamar a la función para ejecutarla
area_cuad(4,6)
```
Función para calcular el volumen de un prisma rectangular:
```r
area_prisma <. function(arista1, arista2, arista3) {
    arista1 * arista2 * arista3
}
# ejecutar la función
area_prisma(3, 6, 9)
```
Escribir otra función aprovechando la función `area_cuad`:
```r
area_prisma <- function(arista1, arista2, arista3) {
    area_cuad(arista1, arista2) * arista3
}
# probar la función
area_prisma(3,6,9)
```

#### Definiendo la función `crear_histograma()`
Definiremos una función con el nombre `crear_histograma()` para generar un gráfica con las
especificaciones que se nos han pedido.

Partimos de una función sin argumentos y el cuerpo vacío:
```r
crear_histograma <- function() {

}
```
Para esta función necesitaremos:
- Los datos que serán graficados
- El nombre de la variable graficada

Por lo tanto, nuestros argumentos serán:
- `datos`
- `nombre`

```r
crear_histograma <- function(datos, nombre) {
    media <- mean(datos)
    des_est <- sd(datos)

    hist(datos, main=nombre, xlab="Datos", ylab="Frecuencia", col="gold")
    abline(v=media), col="red"
    abline(v=media + (des_est * c(1, -1)), col="blue")
}
# generar datos
ingreso = rnomr(1500, mean=15000, sd=45000)
crear_histograma(ingreso, "Ingreso")
```
Ampliación de la función:
```r
crear_histograma <- function(datos, nombre) {
    media <- mean(datos)
    des_est <- sd(datos)
    mediana <- median(datos)

    hist(datos, main=nombre, xlab="Datos", ylab="Frecuencia", col="orange")
    abline(v=media, col="red")
    abline(v=media + (des_est * c(1, -1)), col="blue")
    abline(v=mediana, col="greeen")
}
# ejecutar función
crear_histograma(peso, "Peso con mediana")
```
La función `mean()` calcula el promedio:
```r
notas <- c(4.0, 1.3, 3.8, 2.0)
mean(notas)
```
Usar la función `with()` para extraer un subconjunto:
```r
with(mi_marco, mi_marco[edad >= 15 & deporte == TRUE, ]
```
#### Funciones sobre vectores
En R podemos destacar las siguientes funciones básicas sobre vectores numéricos:
- `min`: para obtener el mínimo de un vector
- `max`: para obtener el máximo de un vector
- `length`: para determinar la longitud de un vector
- `range()`: obtener el rango de valores de un vector, entrega el mínimo y el máximo.
- `sum`: entrega la suma de todos los elementos de los vectores
- `prod`: multiplica todos los elementos del vector
- `which.min`: retorna la posición en donde está el valor mínimo del vector
- `which.max`: retorna la posición máxima del vector
- `rev`: invierte un vector

```r
# crear un vector
my_vect <- c(5, 3, 2, 1, 2, 0, NA, 0, 9, 6)
min(my_vect) # no aparece el cero, sino NA
min(my_vect, na.rm=TRUE) # na.rm remueve los NA
max(my_vect, na.rm=TRUE) # retorna el valor máximo
length(my_vect) # retorna el largo del vector
range(my_vect, na.rm=TRUE) # retorna el mínimo y el máximo
sum(my_vect, na.rm=TRUE) # retorna la suma de todos los elementos del vector
which.min(my_vect) # retorna la posición del número mínimo
which.max(my_vect) # posición del número máximo
```

#### Funciones matemáticas
Algunas funciones básicas utilizadas en estadística son: `sin, cos, tan, asin, acos, atan, atan2,
log, logb, log10, exp, sqrt, abs`.

```r
# ejemplos de medidas trigonométricas
angulos <- c(0, pi/2, pi)
sin(angulos)
tan(angulos)
# logaritmos
log(100)
log10(200)
logb(100)
# exponencial
exp(1)
exp(2)
exp(1:3)
# raices
sqrt(49)
27 ^ (1/3) # raíz cuadrada de 27
# valor absoluto
abs(2.5)
abs(-3.6)
```

#### Función `seq`
En R podemos crear secuencias de números de una forma sencilla con `seq()`, la sintaxis es:
```r
seq(from=1, to=1, by, length.out)
```
Los argumentos de la función son:
- `from`: valor de inicio de la secuencia
- `to`: valor final de la secuencia, no siempre se alcanza
- `by`: incremento de la secuencia
- `length.out`: longitud deseada de la secuencia

```r
# once valores igualmente espaciados desde 0 hasta 1
seq(0, 1, length.out=11)
# secuencia de 2 en 2 comenzando en 1
seq(1,9,2)
# desde el 1 con salto de pi sin pasar del 9
seq(1,9,pi)
# usar : para generar secuencias de rango
2:8
pi:6 # secuencia real
6:pi # secuencia entera
```

#### Función `rep`
La función `rep` permite crear repeticiones y la sintaxis es:
```r
rep(x, times=1, length.out=NA, each=1)
```
Los argumentos para esta función son:
- `x`: vector con los elementos a repetir
- `times`: número de veces que el vector `x` se debe repetir
- `length.out`: longitud deseada para el vector resultante
- `each`: número de veces que cada elemento de `x` se debe repetir

```r
# recrear las siguientes repeticiones
# 12341234
# 11223344
# 112334
# 11223344
rep(1:4, times=2)
rep(1:4, times=c(2,2,2,2))
rep(1:4, times=c(2,1,2,1))
rep(1:4, each=2)
```

#### Funciones `round`, `ceiling`, `floor` y `trunc`
Estas cuatro funciones permiten modificar u obtener información de un número.

- `round(x, digits)`: sirve para redonder un número según los dígitos indicados
- `ceiling(x)`: entrega el mínimo entero mayor o igual que `x`
- `floor(x)`: entrega el máximo entero menor o igual que `x`
- `trunc(x)` entrega la parte enter de un número `x`

```r
x <- 5.34896 # número positivo elegido
round(x, digits=3)
ceiling(x) # retorna 6
floor(x) # retorna 5
trunc(x) # 5
x <- -4.26589 # número negativo
round(x, digits=3)
ceiling(x) # retorna -4
floor(x) # retorna -5
trunc(x) # -5
```

#### Funciones `sort` y `rank`
Las funciones `sort` y `rank` son útiles para ordenar elementos de un vector o para saber posiciones
que ocuparían los elementos de un vector al ser ordenado. La estrucutra es la siguiente:
```r
sort(x, decreasing=FALSE)
rank(x)
```
En `x` es para ingresar el vector y el parámetro `decreasing` sirve para indicar si el ordenamiento es
de menor a mayor (por defecto) o de mayor a menor.

```r
x <- c(2, 3, 6, 4, 9, 5)
sort(x)
sort(x, decreasing=TRUE)
rank(x)
```

#### Más funciones
```r
# return solo funciona en las funciones
suma <- function(x, y) {
    resultado <- x + y
    return(resultado)
}
# compactar
suma <- function(x, y) {
    return(x + y)
}
# compactar
suma <- function(x, y) x + y
# example1
fun1 <- function() {
    num <- runif(1)
    veces <- 1
    while(sum(num) < 3) {
        veces <- veces + 1
        num[veces] <- runif(1)
    }
    return(veces)
}
fun1() # prueba
# example2
fun2 <- function(cota=1) {
    num <- runif(1)
    while(sum(num) < cota) {
        sum <- c(num, runif(1))
    }
    resultado <- list(vector=num, suma=sum(num), cantidad=length(num))
    return resultado
}
fun2() # sin argumento
fun2(cota=3)
# example3
# cat permite concatenar y presentarlos en pantalla
media <- function(a, b) {
    media <- (a + b) / 2
    cat("El punto medio de los valores", a, "y", b, "ingresado es:", media)
}
media(a=-3, b=-1)
```

## Instrucciones de control
```r
# if
sal <- 3500 # salario base por semana
hlab <- 62 # horas laboradas por semana
# condición
if(hlab > 48) {
    hora_extra <- hlab - 48
    salario_extra <- hora_extra * 600
    sal <- sal + salario_extra
}
sal # retorna el nuevo valor

# if else
# exampl
if(condición) {
    operación
    operación
    operación_final
}
else {
    operación
    operación
    operación_final
}

# ifelse: cuando hay una sola condición para if y else
x <- c(1:10)
ifelse(x %% 2 == 0, "Es par", "Es impar")

# for
objeto <- 1:10
for(i in objeto) {
    print(i)
}
# otro ejemplo
nrep <- 10
n <- 100
conteo <- numeric(nrep) # vector para almacenar el conteo
for(i in 1:nrep) {
    x <- runif(n=n, min=1, max=3)
    conteo[i] <- sum(x >= 2.5)
}
conteo # retorna el resultado

# while
# usar sample para simular un lanzamiento
resultados <- c("Cara", "Sol")
sample(x=resultados, size=1)
# ampliación usando while
num.lanza <- 0
num.caras <- 0
historial <- NULL # vector vacío para historial
while(num.caras < 5) {
    res <- sample(x=resultados, size=1)
    num.lanza <- num.lanza + 1
    historial[num.lanza] <- res
    if(res == "Cara") {
        num.caras <- num.caras + 1
    }
}
historial # retorna el historial
num.lanza # retorna la cantidad de lanzamientos

# repeat: repite una condición hasta que se cumpla
x <- 3 # valor de inicio
repeat {
    print(x)
    x <- x + 1
    if(x == 8) {
        break
    }
}
# imprime el resultado hasta el 7

# break interrumpe y next avanza
# intereumpir cuando i sea igual a 3
for(i in 1:10) {
    if(1 == 3) {
        break
    }
    print(i)
}
# con while
numero <- 20
while(numero > 5) {
    if(numero == 15) {
        break
    }
    print(numero)
    numero <- numero - 1
}
# next: permite saltarse una iteración en el bucle
for(i in 1:4) {
    if(i == 3) {
        next
    }
    print(i)
}
# break es necesario para repeat
```

## Lectura de base de datos
Cómo leer bases de datos externas en R.

#### Función `read.table`
La función `read.table()` permite leer bases de datos en R.

La sintaxis es la siguiente:
```r
read.table(file, header, sep, dec)
```
Los argumentos para `read.table()` es:
- `file`: nombre o ruta de los datos. url o path loca
- `file.choose()`: permite abrir una ventana para seleccionar el archivo
- `header`: valor Lógico, se usa `TRUE` si la primera línea son encabezado
- `sep`: tipo de separador en los datos
- `col.name`: un vector opcional, con los nombres de las columnas en la tabla
- `stringAsFactors`: esta función convierte automáticamente los datos de texto a factores
- `dec`: símbolo con el cual están indicados los decimales

```r
# leer archivo CSV
datos <- read.table(file="base1.csv", header=TRUE, sep=",")
# read.csv: acepta los mismos parámetros que read.table, pero en la mayoria de los casos
# solo requiera la ruta del archivo
datos <- read.csv("base1.csv")
# leer archivo TXT con separador
datos <. read.table(file="base1.txt", header=TRUE, sep=" ")
# leer archivo TXT con tabuladores \t
datos <- read.table(file="base2.txt", header=TRUE, sep="\t")

# leer una base de datos desde una URL
url <- 'https://raw.githubusercontent.com/fhernanb/datos/master/aptos2019'
datos <- read.table(file=url, header=TRUE)

# descargar datos con download.file()
download.file(
url = 'url',
destfile = "nombre del archivo para guardar"
mode = "wb" # asegura que el archivo se descargue correctament
)
readLines("BD_Excel.xlsx", n=5) # retorna error porque no es una tabla rectangular
file.show("BD_Excel.xlxs") # abre el archivo
excel_sheets("BD_Excel.xlsx") # nombre de las pestañas como vector
```

#### Leer archivo Excel
Algunas veces los datos están disponibles en un arcvhivo estándar de Excel, y dentro de cada
archivo hojas con la información a utilizar. En estos casos se recomienda usar el paquete
**readxl** y en particular `readxl`.

`read_execl()` tiene los siguientes argumentos:
- `path`: la ruta del archivo, por defecto es el directorio actual
- `sheet`: nombre de la pestaña a importar. Si no se especifica, se leera la primera hoja
- `range`: cadena de texto con el rango de celdas a importar. Por ejemplo: "A1:B10"
- `col.names`: recibe un vector con los nombres para las columnas. Por defecto es `TRUE`. En caso de no tener encabezado, se puede usar esta función.

```r
# instalar el paquete readxl
install.packages("readxl")
library(readxl)
hijos <- read_excel("BD_Excel.xlsx", sheet="Hijos")
as.data.frame(hijos)
padres <- read_excel("BD_Excel.xlsx", sheet="Padres")
as.data.frame(padre)
# es posible usar head() y tail()
head(padres)
head(padre, 4) # las primeras 4 líneas
```

## Exportar datos
Un paso muy importante en el trabajo con R es exportar los datos que hemos generado.

#### Data Frames y matrices
Si nuestros datos se encuentran contenidos en una estructura de datos rectangular, podemos
exportarlos con diferentes funciones.

La función `write.table()` nos permite exportar matrices o data frames, como archivos de texto con
distintas extensiones.

Los argumentos más usados de `write.table()` son:
- `x`: el nombre del data frame o matriz a exportar
- `file`: nombre, extensión y ruta del archivo a guardar. Si se omite, se crear en el directorio actual
- `sep`: delimitador
- `row.names`: para incluir el nombre de los renglones, usar `TRUE`. Se recomienda fijar `FALSE`
- `col.names`: para incluir el nombre de las columnas, establecer en `TRUE`

```r
# exportar a TXT
write.table(mi_marco, "salida.txt", sep=",", col.names=TRUE)
# leer para ver el resultado
read.table("salida.txt", header=TRUE, sep",")
# para el caso de CSV está write.csv()
write.csv(mi_marco, "salida.csv", row.names=FALSE) # los nombres de columnas van por defecto
```

#### Listas
La forma más sencilla de exportar listas es en un archivo RDS. Este es un tipo de archivo nativo
de R que puede almacenar cualquier objeto a un archivo en nuestro disco.

Además, RDS comprime los datos que almacena, por lo que ocupa menos espacio en disco.

Para esto usamos la función `saveRDS()` la cual pide dos argumentos:
- `object`: el nombre del objeto a exportar
- `file`: nombre y ruta del archivo a guardar. Los archivos deben tener la extensión `.rds`

```r
# crear una lista con dos vectores y dos matrices
mi.lista <- list("a"=c(TRUE, FALSE, TRUE),
"b"=c("a", "b", "c",
"c"=matrix(1:4, ncol=2),
"d"=matrix(1:6, ncol=3)))
# guardar el objeto
saveRDS(object=mi.lista, file="mi_lista.rds")
# para leer un archivo RDS, usar la función readRDS() con la ruta del archivo
mi.lista.import <- readRDS("mi_lista.rds")
```

#### Datos de paquetes estadísticos comerciales (SPSS, SAS, STATA)
En Psicología el paquete SPSS Statistic de IBM  es el paquete estadístico más usado (archivos `.sav`).

```r
# instalar el paquete "haven"
install.packages("haven")
library(haven)
```
Todas estas funciones nos piden como argumento la ruta y el nombre del archivo

- `read_spss()`: SPSS Statistic, archivos con extensión sav, zsav y por
- `read_sav()`: SPSS Statistic, solo archivos sav y zsav
- `read_sas()`: SAS, archivos sas7bda
- `read_xpt()`: SAS, archivos xpt
- `read_stata()`: Stata, archivos dta

Todos importan los datos como un data frame.

Para exportar:
- `write_sav()`: SPSS Statistic. archivos sav, zsav o por
- `write_sas()`: SAS, archivos sas7bda
- `write_xpt()`: SAS, archivps xpt
- `write_dta()`: Stata, archivos dta
