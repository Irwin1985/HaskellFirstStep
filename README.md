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
