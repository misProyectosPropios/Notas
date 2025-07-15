Queremos demostrar que ciertas expresiones son equivalentes.
### ¿Para qué?
+ Justificar que un algoritmo es correcto
	+ `∀xs :: [Int]. quickSort xs = insertionSort xs`
	  da confianza relativa de un algoritmo con respecto al otro.
+ Posibilitar optimizaciones

## Hipótesis de trabajo
+ Trabajamos con estructuras de **datos finitas** (técnicamente con **tipos de datos inductivos**)
+ Que trabajamos con **funciones totales**.
	+ Las ecuaciones deben cubrir todos los casos.
	+ La recursión siempre debe terminar
+ El programa **no depende del orden de las ecuaciones**

### Igualdades por definición
Sea `e1 = e2` una ecuación incluida en el programa.
Las siguientes operaciones preservan la igualdad de expresiones:
1. Reemplazar **cualquier instancia** de e1 por e2.
2. Reemplazar **cualquier instancia** de e2 por e1.

>Si una igualdad se puede demostrar usando solo el principio de reemplazo, decimos que la igualdad vale por definición.


## Inducción estructural
### Inducción sobre booleanos

Si P(True) y P(False) entonces ∀x :: Bool. P(x).
### Inducción sobre pares

Si ∀x :: a. ∀y :: b. P((x, y)), entonces ∀p :: (a, b). P(p).
### Inducción sobre naturales
```haskell
data Nat = Zero | Succ Nat
```

Si P(Zero) y ∀n :: Nat. (P(n) => P(succ(n))) siendo P(n) la **hipótesis inductiva** y P(succ(n)) la **tesis inductiva**

Entonces ∀n :: Nat. P(n).

### Inducción estructural (general)

Si tenemos un tipo de dato genérico

```haskell
data T = CBase1 (parámetros)
. . .
| CBasen (parámetros)
| CRecursivo1 (parámetros)
. . .
| CRecursivom (parámetros)
```

Sea P una propiedad acerca de las expresiones tipo T tal que:
+ P vale sobre todos los constructores base de T,
+ P vale sobre todos los constructores recursivos de T, asumiendo como hipótesis inductiva que vale para los parámetros de tipo T,
entonces ∀x :: T. P(x).

Ejemplo:
```haskell
Poli a = X
| Cte a
| Suma (Poli a) (Poli a)
| Prod (Poli a) (Poli a)
```

Sea P una propiedad sobre expresiones de tipo Poli a tal que:
+ P(X)
+ ∀k :: a. P(Cte k)
+ ∀p :: Poli a. ∀q :: Poli a.
	+ ((P(p) ∧ P(q)) (**HI**) => P(Suma p q) (**TI**)
+ ∀p :: Poli a. ∀q :: Poli a
	+ ((P(p) ∧ P(q)) (**HI**) => P(Prod p q) (**TI**)
### Lemas de generación

#### Lema de generación para pares

`Si p :: (a, b), entonces ∃x :: a. ∃y :: b. p = (x, y).`

#### Lema de generación para sumas

```haskell
data Either a b = Left a | Right b
```

Si e :: Either a b, entonces:
+ o bien ∃x :: a. e = Left x
+ o bien ∃y :: b. e = Right y


### Extensionalidad

#### Tipos
+ Punto de vista intensional:
	+ Dos valores son iguales si están construidos de la misma manera
+ Punto de vista extensional:
	+ Dos valores son iguales si son indistinguibles al observarlos.

quickSort e insertionSort
+ no son intensionalmente iguales;
+ sí son extensionalmente iguales: computan la misma función.

#### Propiedades:
##### Propiedad inmediata

`Si f = g entonces (∀x :: a. f x = g x).`
##### Principio de extensionalidad funcional

`Si (∀x :: a. f x = g x) entonces f = g.`

## TLDR de razonamiento ecuacional:

##### Principio de reemplazo
Si el programa declara que e1 = e2, cualquier instancia de e1 es igual a la correspondiente instancia de e2, y viceversa
##### Principio de inducción estructural
Para probar P sobre todas las instancias de un tipo T, basta probar P para cada uno de los constructores (asumiendo la H.I. para los constructores recursivos).
##### Principio de extensionalidad funcional
Para probar que dos funciones son iguales, basta probar que
son iguales punto a punto
## Isomorfismos de tipos

### Definición:
Decimos que dos tipos de datos A y B son isomorfos si:
1. Hay una función f :: A -> B total.
2. Hay una función g :: B -> A total.
3. Se puede demostrar que g . f = id :: A -> A.
4. Se puede demostrar que f . g = id :: B -> B.
> Escribimos A ≃ B para indicar que A y B son isomorfos.


## Casos de estudios

### Demostrar que no vale una propiedad

Buscamos un contraejemplo
Basta con encontrar una observación `obs :: A -> Bool` que las distinga
### Necesidad de lemas auxiliares

Hay algunas propiedades que para demostrarlas es necesario conocer algún lema auxiliar que logra *destrabar* algún paso
