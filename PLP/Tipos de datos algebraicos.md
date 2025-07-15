

Generar nuevos tipos de datos se logra con **`data`**

```haskell
data Tipo = (declaración de los constructores)
```

Un tipo puede ser **recursivo o no**.
+ Si es recursivo, tiene al mismo tipo dentro de la declaración de los constructores.

Todos los [[Tipos de datos algebraicos]] deben de tener una declaración de algún constructor que no sea recursivo, pues sino el tipo no se podría declarar nunca al ser infinito

Ejemplo de **tipo recursivo**:

```haskell
data Nat = Zero
		  | Succ Nat
```

## Caso general:

En general un tipo de datos algebraico tiene la siguiente forma:
```haskell
data T = CBase1 (parámetros)
. . .
| CBasen (parámetros)
| CRecursivo1 (parámetros)
. . .
| CRecursivom (parámetros)
```

+ Los constructores base no reciben parámetros de tipo T
+ Los constructores recursivos reciben al menos un parámetro de tipo T.
+ Los valores de tipo T son los que se pueden construir aplicando constructores base y recursivos un número finito de veces y sólo esos.