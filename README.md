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



