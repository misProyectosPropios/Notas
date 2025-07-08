nombreFuncion :: type -> type -> $\dots$ -> type
nombreFuncion param1 param2 = expresion


data Person = Person String String Int Float String String deriving (Show)

Y si quiero obtener sus tipos, puedo usar record sintaxis:

Y si quiero obtener los valores de un tipo de dato sin hacer todos sus constructores, uso **record sintaxis**
(sin **record sintaxis**)
data Person = Person String String Int Float String String deriving (Show)

(con **record sintaxis**)
data Person = Person { firstName :: String
                     , lastName :: String
                     , age :: Int
                     , height :: Float
                     , phoneNumber :: String
                     , flavor :: String
                     } deriving (Show)
Ambos son lo mismo, solo que el 2do puede obtener los valores de cada tipo sin generar explícitamente los constructores.


## Type parameters

Un constructor e tipos puede tomar parámetros para generar nuevos tipos. 
Por ejemplo, queremos un tipo que sea de un tipo arbitrario que sea o Nothing o un valor de ese tipo (Maybe). Se declararía así:

data Maybe a = Nothing | Just a

## Typeclasses
typeclasses: a que funciones puede llamar dando un tipo de datos arbitrario. Generan restricciones sobre a cuales funciones se puede llamar en Haskell. Son como las interfaces en OOP.

No hacemos la ata desde las typeclasses. Sino, hacemos los tipos de datos y después decidimos sobre lo que pueden tener funciones

Para agregar un typeclass, agregar al final de la creación del data deriving (typeclasses).
> **Observación**: para que sea  válido poner un typeclass, cada uno de los tipos internos debe pertenece al typeclass respectivo. 

## Type synonyms

Para hacer un type synonyms, se usa el type nombreNuevo = OtroTipo

## Recursive data structures

Para generar estructuras de datos recursiva, simplemente, cuando haces data nombreNuevo, al igualarlo, llama de nuevo al nombreNuevo. Lo que sí, deberías de tener un caso base para que se pueda terminar la estructura

## Typeclasses 102

Para generar como deberían de ser las implementaciones, se usa la keyword **instance** 

```haskell
data TrafficLight = Red | Yellow | Green

instance Eq TrafficLight where
    Red == Red = True
    Green == Green = True
    Yellow == Yellow = True
    _ == _ = False

instance Show TrafficLight where
    show Red = "Red light"
    show Yellow = "Yellow light"
    show Green = "Green light"
```

```haskell
instance (Eq m) => Eq (Maybe m) where
    Just x == Just y = x == y
    Nothing == Nothing = True
    _ == _ = False
```

## Input and output
```haskell
main = putStrLn "hello, world"
-- programa que dice 'hello, world' en haskell
-- En windows lo más probable es que no ande
```

Esto solo muestra _"hello, world"_. Para hacer algo más que solo escribir ese texto, podemos usar el do

```haskell
main = do
    putStrLn "Hello, what's your name?"
    name <- getLine
    putStrLn ("Hey " ++ name ++ ", you rock!")
```

El `do` sirve para hacer que todas las acciones IO sean solamente una y poder tener más juego en el programa
Por eso, la función main debe de tener siempre el tipo ` main :: IO something`

### Funciones útiles de input / output para la terminal
1. _**putStrLn**_: escriba en la terminal el String que recibe con una nueva línea al final
2.  _**print**_: escribe en la terminal la variable que reciba si es _printeable_
   > Para los Strings se suele usar el putStrLn para evitar las comillas alrededor del texto
3. _**putStr**_: escribe en la terminal el String que recibe, pero sin una nueva línea al final
4. _**putChar**_: escribe en la termina el Char que recibe
5. _**getLine**_: Recibe un String desde la terminal
	>Se suelen usar con `variable <-` para "guardar" el valor del String en la variable 
6. _**getChar**_: Recibe un Char desde la terminal
	>Al igual que con getLine, suele usarse con `variable <-` por el mismo motivo.

### Funciones útiles de IO para archivos y streams
