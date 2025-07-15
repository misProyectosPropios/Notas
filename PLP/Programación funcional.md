Procesamos información con la programación

![[Pasted image 20250714222113.png]]

### Qué es la programación funcional

+ Consiste en definir funciones y aplicarlas para procesar información

Las **funciones** tienen las siguientes características:
+ Aplicar una función **no tiene efectos secundarios**.
+ A una **misma entrada** corresponde siempre la **misma salida.**
+ Las estructuras de datos son **inmutables**.

Las **funciones** son como un **tipo de dato**, teniendo las siguientes características
+ Se pueden pasar como parámetros.
+ Se pueden devolver como resultados.
+ Pueden formar parte de estructuras de datos

Un **programa funcional** está dado por un conjunto de **ecuaciones orientadas**
Se dice que:
$$e_1 = e_2$$
si:
+ **Vista denotacional.**
	+ Declara que e1 y e2 tienen el mismo significado
+ **Punto de vista operacional**
	+ Computar el valor de e1 se reduce a computar el valor de e2.
Es decir, puede ser si literalmente son lo mismo o si generan los mismos resultados.
## Características de programa funcional:

Está formado por un conjunto de ecuaciones

```haskell
nombre parametros = expresion
```

### Expresiones:
Secuencias de símbolos que sirven para representar datos, funciones y funciones aplicadas a los datos.
*(Recordemos: las funciones tambien son datos).*

#### Tipos:
+ **Constructor**
	+ True; 
	+ False; 
	+ []; 
	+ (:); 
	+ 0; 
	+ 1; 
	+ 2; 
	+ $\dots$;
+ **Variable**:
	+ longitud;
	+ ordenar;
	+ x;
	+ xs;
	+ (+); 
	+ (\*);
+ **Aplicación de una función a otra**
	+ ordenar lista;
	+ not True;
	+ not (not True);
	+ (+) 1.

La aplicación de funciones es **asociativa a izquierda**

```haskell
f x y ≡ (f x) y
f a b c d ≡ (((f a) b) c) d
```

> Hay secuencias de símbolos que no son expresiones bien formadas sintácticamente

```haskell
1,,2
)f x(
```

> Hay expresiones que están bien formadas sintácticamente, pero que no tienen sentido

```
True + 1
0 1
[[], (+)]
```

Un **tipo** es una **especificación del invariante** de un dato o de una
función.

```haskell
99 :: Int
not :: Bool -> Bool
not True :: Bool
```

El tipo de una función expresa un **contrato**.

#### Condiciones de tipado
Para que un programa este bien tipado:
1. Todas las expresiones deben tener tipo.
2. Cada variable se debe usar siempre con un mismo tipo.
3. Los dos lados de una ecuación deben tener el mismo tipo.
4. El argumento de una función debe tener el tipo del dominio.
5. El resultado de una función debe tener el tipo del codominio.

##### **Solo tienen sentido los programas bien tipados.**

##### **Inferencia: no es necesario escribir explícitamente los tipos**

##### El **`->`** es asociativo a derecha:
```haskell
a -> b -> c ≡ a -> (b -> c)
a -> b -> c -> d ≡ a -> (b -> (c -> d))
```

#### Polimorfismo

**Definición**: Expresiones que tienen más de un tipo
Los **tipos desconocidos** son denotados por $\{a,b,...\}$ 

#### Modelo de computo:
Dada una expresión, se computa su valor a través de las ecuaciones.

> Hay expresiones bien tipadas que no tienen un valor. Se indefinen o tienen valor $\bot$
> Ejemplo: `1/0` 

> El lado izquierdo de una ecuación no es una expresión arbitraria.
> Debe ser una función aplicada a patrones.

Un patrón puede ser:
1. Una variable.
2. Un comodín _.
3. Un constructor aplicado a patrones.
> El lado izquierdo no debe tener variables repetidas.

##### Como se evalúa:
Evaluar una expresión consiste en:
1. Buscar la subexpresión más externa que coincida con el lado izquierdo de una ecuación.
2. Reemplazar la subexpresión que coincide con el lado izquierdo de la ecuación por la expresión correspondiente al lado derecho.
3. Continuar evaluando la expresión resultante.

Y el **caso base**:
+ La expresión es un constructor o un constructor aplicado;
	+ True, 
	+ (:) 1
	+ [1,2,3]
+ La expresión es una función parcialmente aplicada;
	+ (+);
	+ (+) 5.
+ Se alcanza un estado de error.
	+ Un estado de error es una expresión que no coincide con las ecuaciones que definen a la función aplicada


Funciones importantes de Haskell:

#### Map
```haskell
map :: (a -> b) -> [a] -> [b]
map f [] = []
map f (x : xs) = f x : map f xs
```
#### Filter
```haskell
filter :: (a -> Bool) -> [a] -> [a]
filter p [] = []
filter p (x : xs) = if p x
					then x : filter p xs
					else filter p xs
```



### Notación lambda
Una expresión de la forma:
```haskell
\x -> e
```
representa una función que recibe un parámetro x y devuelve e.

Notación:
```haskell
(\ x1 x2 ... xn -> e) ≡ (\ x1 -> (\ x2 -> ... (\ xn -> e)))
```

