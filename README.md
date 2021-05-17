# Haskell
Mis apuntes de Haskell

### Operaciones aritméticas
```Haskell
ghci> 2 + 15
17
ghci> 49 * 100
4900
ghci> 1892 - 1472
420
ghci> 5 / 2
2.5
```
### Precedencia de operadores
```Haskell
ghci> (50 * 100) - 4999
1
ghci> 50 * 100 - 4999
1
ghci> 50 * (100 - 4999)
-244950
```
### Algebra booleana
```Haskell
ghci> True && False
False
ghci> True && True
True
ghci> False || True
True
ghci> not False
True
ghci> not (True && True)
False
```
### Operadores de igualdad o desigualdad `==` y `/=` el `distinto de` cambia un poco
```Haskell
ghci> 5 == 5
True
ghci> 1 == 0
False
ghci> 5 /= 5
False
ghci> 5 /= 4
True
ghci> "hello" == "hello"
True
```
### Invocando funciones
Las funciones en `Haskell` pueden engañarte porque no todas son como las conocemos, es decir, `calcularIVA()` para cualquiera es una función válida pero lo cierto es que `Haskell` ofrece también funciones con símbolos como nombres:

`*` es una función que toma 2 números y los multiplica. Y para invocar la función simplemente colocamos el identificador entre los 2 argumentos, a esto se le conoce como funciones infijas. La mayoría de las funciones de hecho son prefijas lo cual quiere decir que el nombre de la función se escribe primero y luego sus argumentos:

```Haskell
ghci> succ 8
9
```
La función `succ` toma un argumento que puede ser cualquier tipo de dato que tenga un sucesor. En este caso el argumento es un entero y por lo tanto tiene sucesores enteros. 1..2..3..4..5..etc.
```Haskell
ghci> min 9 10
9
ghci> min 3.4 3.2
3.2
ghci> max 100 101
101
```
Las funciones `min` y `max` toman un argumento que pueda ser *ordenado* y retornan el más bajo o el más alto de ellos.

`NOTA:` 
- Las funciones en `Haskell` tienen la mayor precedencia de todas.
- Si una función toma 2 argumentos entonces se puede pasar de prefija a infija encerrandola con backticks.
```Haskell
ghci> div 92 10
9
``` 
La expresión anterior se puede pasar de prefija a infija de la siguiente manera:
```Haskell
ghci> 92 `div` 10
9
``` 
#### Definición de funciones
Una función en `Haskell` comienza con la primera letra del identificador en minúsculas seguido de letras y números, luego seguido de 1 espacio se especifican sus parámetros separados también por espacios, seguido del operador `=` que separa la firma de la función de su cuerpo.

```Haskell
--guardar como baby.hs
doubleMe x = x + x
``` 
Luego se puede cargar el fichero anterior y jugar con sus funciones definidas:
```Haskell
ghci> :l baby
[1 of 1] Compiling Main ( baby.hs, interpreted )
Ok, modules loaded: Main.
ghci> doubleMe 9
18
ghci> doubleMe 8.3
16.6
``` 
El condicional `if` en `Haskell` es obligatorio ya que de no cumplirse la condición se tiene que devolver un valor obligatoriamente.
```Haskell
doubleSmallNumber x = if x > 100
                        then x
                        else x*2
``` 
### Introducción a las Listas
Las listas en `Haskell` son estructuras de datos homogeneas, es decir que solo almacenan elementos del mismo tipo. Se definen encerrandolas en corchetes y sus elementos separados por coma.
```Haskell
ghci> let lostNumbers = [4,8,15,16,23,42]
ghci> lostNumbers
[4,8,15,16,23,42]
``` 
### Concatenación de listas
Con el operador `++` se pueden concatenar 2 o más listas y generar una nueva lista con la suma de todas.
```Haskell
ghci> [1,2,3,4] ++ [9,10,11,12]
[1,2,3,4,9,10,11,12]
ghci> "hello" ++ " " ++ "world"
"hello world"
ghci> ['w','o'] ++ ['o','t']
"woot"
``` 
`NOTA:` En `Haskell` las cadenas son realmente listas de caracteres. Por ejemplo, la cadena "Irwin" es de hecho una lista con la siguiente estructura: `['I', 'r', 'w', 'i', 'n']`. Gracias a esto podemos usar las funciones aplicadas a las listas en las cadenas también.
```Haskell
ghci> 'A':" SMALL CAT"
"A SMALL CAT"
ghci> 5:[1,2,3,4,5]
[5,1,2,3,4,5]
``` 
El operador `:` toma un argumento a su izquierda y lo introduce en el segundo argumento de su derecha. Normalmente el argumento de la izquierda es un item cuyo tipo de dato es el mismo que el de la lista de la derecha.
Por otro lado el operador `++` siempre toma 2 listas y las concatena, incluso si una de ellas está conformada por 1 solo elemento o está vacía.
```Haskell
ghci> [1,2,3,4] ++ [5]
[1,2,3,4,5]
``` 
### Accediendo a los elementos de una lista
Para acceder a un elemento de una lista por su índice, se tiene que usar el operador `!!`. El índice de una lista comienza por cero al igual que en muchos lenguajes de programación.
```Haskell
ghci> "Steve Buscemi" !! 6
'B'
ghci> [9.4,33.2,96.2,11.2,23.25] !! 1
33.2
``` 
`NOTA:` si intentas acceder mediante un índice que no existe en la lista entonces tendrás un error.
### Listas de listas
Las listas pueden contener otras listas que contienen otras listas, etc.
```Haskell
ghci> let b = [[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]
ghci> b
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]
ghci> b ++ [[1,1,1,1]]
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3],[1,1,1,1]]
ghci> [6,6,6]:b
[[6,6,6],[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]]
ghci> b !! 2
[1,2,2,3,4]
``` 
### Comparando listas
Las listas pueden ser comparadas siempre y cuando sus elementos sean comparables. Los operadores de comparación `<, <=, >, >=` comparan dos listas en orden lexicográfico, esto quiere decir que primero se comparan sus 2 cabezas y si son iguales entonces se compara el siguiente elemento de ambas listas y si son iguales entonces el siguiente, etc.
```Haskell
ghci> [3,2,1] > [2,1,0]
True
ghci> [3,2,1] > [2,10,100]
True
ghci> [3,4,2] < [3,4,3]
True
ghci> [3,4,2] > [2,4]
True
ghci> [3,4,2] == [3,4,2]
True
``` 
### Más operaciones sobre listas
La función `head` toma una lista como argumento y devuelve su cabeza o el primer elemento.
```Haskell
ghci> head [5,4,3,2,1]
5
``` 
La función `tail` toma una lista como argumento y devuelve su cola, es decir, todo el cuerpo excepto su cabeza.
```Haskell
ghci> tail [5,4,3,2,1]
[4,3,2,1]
``` 
La función `last` toma una lista como argumento y devuelve su último argumento.
```Haskell
ghci> last [5,4,3,2,1]
1
``` 
La función `init` toma una lista como argumento y devuelve todos sus argumentos excepto el último.
```Haskell
ghci> init [5,4,3,2,1]
[5,4,3,2]
``` 
La función `length` toma una lista como argumento y devuelve su tamaño que es el número total de sus elementos.
```Haskell
ghci> length [5,4,3,2,1]
5
``` 
La función `null` chequea si una lista está vacía.
```Haskell
ghci> null [1,2,3]
False
ghci> null []
True
``` 
La función `reverse` toma una lista como argumento y la devuelve con su orden invertido.
```Haskell
ghci> reverse [5,4,3,2,1]
[1,2,3,4,5]
``` 
La función `take` toma un número y una lista. Extrae el número especificado de elementos de la lista comenzando por la cabeza.
```Haskell
ghci> take 3 [5,4,3,2,1]
[5,4,3]
ghci> take 1 [3,9,3]
[3]
ghci> take 5 [1,2]
[1,2]
ghci> take 0 [6,6,6]
[]
``` 
Si el número de elementos a tomar es mayor a la lista entonces se devuelve toda la lista y si el número es cero entonces devuelve la lista vacía.

La función `drop` toma un número y una lista. Elimina el número especificado de elementos de la lista comenzando por la cabeza.
```Haskell
ghci> drop 3 [8,4,2,1,5,6]
[1,5,6]
ghci> drop 0 [1,2,3,4]
[1,2,3,4]
ghci> drop 100 [1,2,3,4]
[]
``` 
La función `maximun` toma una lista y devuelve su elemento más alto.
```Haskell
ghci> maximum [1,9,2,3,4]
9
ghci> minimum [8,4,2,1,5,6]
1
``` 
La función `sum` toma una lista y devuelve la suma de sus elementos.
```Haskell
ghci> sum [5,2,1,6,3,2,5,7]
31
``` 
La función `product` toma una lista y devuelve el producto de sus elementos.
```Haskell
ghci> sum [5,2,1,6,3,2,5,7]
31
``` 
La función `elem` toma un elemento y una lista y nos dice si ese elemento existe en la lista. Se puede leer mejor en la forma infija:
```Haskell
ghci> 4 `elem` [3,4,5,6]
True
ghci> 10 `elem` [3,4,5,6]
False
``` 
### Rangos
Los rangos son muy sencillos, simplemente si queremos una secuencia numérica del 1 al 20 decimos `[1..20]`. 
```Haskell
ghci> [1..20]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
ghci> ['a'..'z']
"abcdefghijklmnopqrstuvwxyz"
ghci> ['K'..'Z']
"KLMNOPQRSTUVWXYZ"
``` 
Incluso se puede especificar el intervalo entre los elementos del rango:
```Haskell
ghci> [2,4..20]
[2,4,6,8,10,12,14,16,18,20]
ghci> [3,6..20]
[3,6,9,12,15,18]
``` 
La función `cycle` toma una lista y replica sus elementos indefinidamente. Para detenerla solo hace falta usar una otra función como `take` para que se detenga al extraer los N elementos especificados.
```Haskell
ghci> take 10 (cycle [1,2,3])
[1,2,3,1,2,3,1,2,3,1]
ghci> take 12 (cycle "LOL ")
"LOL LOL LOL "
``` 
La función `repeat` toma un elemento y produce una lista infinita de ese elemento. Para detenerla solo hace falta usar una otra función como `take` para que se detenga al extraer los N elementos especificados.
```Haskell
ghci> take 10 (repeat 5)
[5,5,5,5,5,5,5,5,5,5]
``` 
La función `replicate` toma una longitud y un elemento y produce una lista de tal elemento con tal longitud.
```Haskell
ghci> replicate 3 10
[10,10,10]
``` 
### Comprensión de listas
Son una forma de filtrar, transformar y combinar listas.
```Haskell
ghci> [x*2 | x <- [1..10]]
[2,4,6,8,10,12,14,16,18,20]
``` 
El ejemplo anterior itera sobre una lista de 10 elementos `[1..10]` y por cada uno genera la salida `x*2` que basicamente multiplica el elemento por 2.
```Haskell
ghci> [x*2 | x <- [1..10], x*2 >= 12]
[12,14,16,18,20]
``` 
Este otro ejemplo itera sobre una lista de 10 elementos pero solo imprime aquellos mayores o iguales a 12. Note como se usa la expresión `x*2` en el predicado.
Una comprensión de listas puede tomar cero, uno o más predicados separados por coma.

### Tuplas
Las tuplas se utilizan para almacenar elementos heterogéneos. En cierta forma son parecidas a las listas pero con diferencias fundamentales. La primera es que pueden contener elementos heterogéneos y la segunda es que su longitud es fija, por lo tanto hay que conocer su tamaño de antemano.

Las listas se definen entre parentesis y sus elementos se separan por coma:
```Haskell
ghci> (1, 3)
(1,3)
ghci> (3, 'a', "hello")
(3,'a',"hello")
ghci> (50, 50.4, "hello", 'b')
(50,50.4,"hello",'b')
``` 

### Usando Pares
Almacenar datos en pares es muy común en `Haskell` y cuando es el caso hay funciones que nos permiten manipularlos, tales funciones son:

La función `fst` toma un par y retorna su primer componente.
```Haskell
ghci> fst (8, 11)
8
ghci> fst ("Wow", False)
"Wow"
``` 
La función `snd` toma un par y retorna el segundo componente.
```Haskell
ghci> snd (8, 11)
11
ghci> snd ("Wow", False)
False
``` 
`NOTA:` estas funciones solo trabajan con tuplas pares.

La función `zip` toma 2 listas y les aplica un join formando elementos pares entre ambas listas produciendo una tercera lista.
```Haskell
ghci> zip [1,2,3,4,5] [5,5,5,5,5]
[(1,5),(2,5),(3,5),(4,5),(5,5)]
ghci> zip [1..5] ["one", "two", "three", "four", "five"]
[(1,"one"),(2,"two"),(3,"three"),(4,"four"),(5,"five")]
``` 
Si la longitud de ambas listas es distinta entonces aplica el join sobre los elementos que encajen:
```Haskell
ghci> zip [5,3,2,6,2,7,2,5,4,6,6] ["im","a","turtle"]
[(5,"im"),(3,"a"),(2,"turtle")]
``` 


