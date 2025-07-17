## Introducción

### Diferencia entre lógica proposicional y de primer orden

#### Lógica proposicional
Permite razonar acerca de proposiciones.

### Lógica de primer orden
Permite razonar acerca de elementos sobre los que se predica.
Extiende a la lógica proposicional con **términos** y **cuantificadores**
### Usos de la lógica en la computación
Conexión estrecha entre lógica de primer orden y computación.
**Históricamente**
+ Problema de la decisión de Hilbert.
**Actualidad**
+ Computabilidad y complejidad descriptiva.
+ Representación del conocimiento, sistemas multi-agente.
+ Inteligencia artificial, razonamiento automático.
+ Métodos formales, verificación automática.
+ Bases de datos relacionales, lenguajes de consulta.
+ Verificación de hardware.
+ $\dots$
+ Fundamento de la programación lógica.

## Sintaxis de la lógica de primer orden

#### Lenguajes de primer orden

Un **lenguaje de primer orden** L está dado por:
+ Un **conjunto de símbolos de función** $\mathcal{F} = \{f,g,h, \dots\}$
  Cada símbolo de función tiene asociada una **aridad** (≥ 0).
  Los símbolos de función de aridad 0 se llaman **constantes**.
+ Un **conjunto de símbolos de predicado** $\mathcal{P} = \{f,g,h, \dots\}$.
  Cada símbolo de predicado tiene asociada una aridad (≥ 0).

#### Términos de primer orden

El conjunto T de términos se define por la siguiente gramática:

$$t ::= X \text{ | } f(t_1, \dots , t_n)$$


#### Fórmulas de primer orden

```haskell
σ ::= P(t1, . . . , tn)          fórmula atómica
	| ⊥                          contradicción
	| σ ⇒ σ                      implicación
	| σ ∧ σ                      conjunción
	| σ ∨ σ                      disyunción
	| ¬σ                         negación
	| ∀X. σ                      cuantificación universal
	| ∃X. σ                      cuantificación existencial
```

> P denota un símbolo de predicado de aridad n.
> Los cuantificadores ligan una variable X.

##### Ocurrencia libre o ligada

Una **ocurrencia** de una variable X en una fórmula está:
+ **ligada** si está bajo el alcance de un cuantificador $\forall text{ X / } \exists \text{ X }$,
+ libre si no.

##### Sustitución

Notamos $\sigma\{X := t\}$  a la sustitución de las ocurrencias libres de X
en la fórmula σ por el término t, evitando la captura de variables.
## Deducción natural para lógica de primer orden

La deducción natural proposicional se extiende a primer orden.
1. Un **contexto** $\Gamma$ es un conjunto finito de fórmulas.
2. Un **secuente** es de la forma $\Gamma \vdash \sigma$.
### Reglas

Se agregan reglas de introducción y eliminación para ∀ y ∃.

`Axioma                               ax        `
`Conjunción                           ∧i ∧e1 ∧e2`
`Disyunción                           ∨i1 ∨i2 ∨e`
`Implicación                          ⇒i ⇒e     `
`Negación                             ¬i ¬e     `
`Contradicción                        ⊥e        `
`Lógica clásica                       ¬¬e       `
`Cuantificación universal             ∀i ∀e     `
`Cuantificación existencial           ∃i ∃e     `
### Justificación de las restricciones al agregar las nuevas reglas

## Semántica de la lógica de primer orden

### Estructuras de primer orden

#### Definición
Una **estructura de primer orden** es un par $\mathcal{M}$  = (M, I ) donde:
+ *M* es un **conjunto no vacío**, llamado **universo**
+ *I* es una **función** que le da una **interpretación a cada símbolo**.
+ Para cada símbolo de función f de aridad n:
$$I (f) : M^n \rightarrow M$$
+ Para cada símbolo de predicado P de aridad n:
$$(P) \subseteq M^n$$
### Interpretación de términos
#### Asignación
Una asignación es una función que a cada variable le asigna un elemento del universo:

$$ a : \mathcal{X} → M$$
#### Interpretación de términos

Cada termino $t \in T$ se interpreta como un elemento $a(t) \in M$,
extendiendo la definición de **a** a términos:
$$ a(f(t_1, \dots , t_n)) = I(f)(a(t_1), \dots , a(t_n)) $$
#### Satisfacción

Definimos una relación de satisfacción $a \vDash_M \sigma$.
> “La asignación a (bajo la estructura M) satisface la fórmula $\sigma$”.

![[Pasted image 20250716232836.png]]
#### Validez y satisfactibilidad

![[Pasted image 20250716232847.png]]

### Modelos

#### Sentencia
Una **sentencia** es una **fórmula** $\sigma$ **sin variables libres**.
#### Teoría
Una **teoría** de primer orden es un **conjunto de sentencias**.
#### Consistencia

Una teoría T es **consistente** si $T \nvdash \bot$.
#### Modelo

Una estructura $\mathcal{M}= (M, I)$ es un modelo de una teoría $\mathcal{T}$ si vale
$\vDash_{\mathcal{M}} \sigma$ para toda fórmula $\sigma \in \mathcal{T}$ 
> La asignación es irrelevante pues σ es cerrada.

### Corrección y completitud

### Problema de la decisión
## Unificación de términos

### Algoritmo

![[Pasted image 20250716233403.png]]

### Correctitud del algoritmo

