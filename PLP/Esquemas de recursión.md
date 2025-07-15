## Recursión estructural
Sea `g :: [a] -> b` definida por dos ecuaciones:

```haskell
g [] = (caso base)
g (x : xs) = (caso recursivo)
```

La definición de `G` está definida por **recursión estructural** si:
1. El caso base devuelve un valor z “fijo” (no depende de g).
2. El caso recursivo no puede usar los parámetros g ni xs, salvo en la expresión (g xs):

```haskell
g [] = z
g (x : xs) = . . . x . . . (g xs) . . .
```

Ejemplo de función que es recursión estructural:

```haskell
suma :: [Int] -> Int
suma [] = 0
suma (x : xs) = x + suma xs
```

Ejemplo de función que **no** es recursión estructural:
```haskell
ssort :: Ord a => [a] -> [a]
ssort [] = []
ssort (x : xs) = minimo (x : xs)
				: ssort (sacarMinimo (x : xs))
```

### foldr

Abstrae el esquema de recursión estructural

```haskell
foldr f z [] = z
foldr f z (x : xs) = f x (foldr f z xs)
```

El **tipo** de `foldr` es **`foldr :: (a -> b -> b) -> b -> [a] -> b`**

> Toda recursión estructural es una instancia de foldr.
## Recursión primitiva

Sea `g :: [a] -> b` definida por dos ecuaciones:

```haskell
g [] = (caso base)
g (x : xs) = (caso recursivo)
```

Decimos que la definición de `g` está dada por recursión primitiva si:
1. El caso base devuelve un valor z “fijo” (no depende de g).
2. El caso recursivo no puede usar el parámetro g, salvo en la expresión (g xs).
   **Sí puede usar el parámetro xs**

```haskell
g [] = z
g (x : xs) = . . x . . . xs . . . (g xs) . . .
```

> Como la recursión estructural, solo que deja usar el parámetro `xs`


#### Observaciones:
+ Todas las definiciones dadas por recursión estructural tambien están dadas por recursión primitiva.
+ Hay definiciones dadas por recursión primitiva que no están dadas por recursión estructural.

### recr

```haskell
recr f z [] = z
recr f z (x : xs) = f x xs (recr f z xs)
```

El **tipo** de `recr` es **`recr :: (a -> [a] -> b -> b) -> b -> [a] -> b

## Recursión iterativa

Sea `g :: b -> [a] -> b` definida por dos ecuaciones:

```haskell
g ac [] = (caso base)
g ac (x : xs) = (caso recursivo)
```


Decimos que la definición de `g` está dada por **recursión iterativa** si:
1. El caso base devuelve el acumulador ac.
2. El caso recursivo invoca inmediatamente a (g ac’ xs), donde ac’ es el acumulador actualizado en función de su valor anterior y el valor de x.
### foldl

```haskell
foldl f ac [] = ac
foldl f ac (x : xs) = foldl f (f ac x) xs
```

> Toda recursión iterativa es una instancia de foldl.


##### **En general foldr y foldl tienen comportamientos diferentes:**

```haskell
foldr (*) z [a, b, c] = a * (b * (c * z))
foldl (*) z [a, b, c] = ((z * a) * b) * c
```

> Si `*` es un operador asociativo y conmutativo, generan lo mismo


### Datos algebraicos y recursión

Una vez definimos los [[Tipos de datos algebraicos]], podemos generar un tipo de **recursión estructural general**, tal que no sea únicamente para las listas, sino para cualquier  [[Tipos de datos algebraicos]].

#### Esquema de recursión estructural general

Dada una función g :: T -> Y definida por ecuaciones:

```haskell
g (CBase1 (parámetros)) = (caso base1)
. . .
g (CBasen (parámetros)) = (caso basen)
g (CRecursivo1 (parámetros)) = (caso recursivo1)
. . .
g (CRecursivom (parámetros)) = (caso recursivom)
```

Decimos que g está dada por **recursión estructura**l si:
1. Cada caso base se escribe combinando los parámetros.
2. Cada caso recursivo:
	1. No usa la función g.
	2. No usa los parámetros del constructor que son de tipo T.
	3. Hacer llamados recursivos sobre parámetros de tipo T.
	4. Usar los parámetros del constructor que no son de tipo T.

###### Ejemplo:
```haskell
data AB a = Nil
			| Bin (AB a) a (AB a)
```

```haskell
foldAB :: b -> (b -> a -> b -> b) -> AB a -> b
foldAB cNil cBin Nil = cNil
foldAB cNil cBin (Bin i r d) =
		cBin (foldAB cNil cBin i) r (foldAB cNil cBin d)
```