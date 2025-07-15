Queremos poder hacer afirmaciones matemáticamente precisas sobre programas en distintos lenguajes de programación

##### Ejemplos de afirmaciones que querríamos hacer
+ El tipo (Bool -> Int) está sintácticamente bien formado.
+ La expresión map tiene tipo ((a -> b) -> [a] -> [b]).
+ La expresión map tiene tipo ((a -> a) -> [a] -> [a]).
+ La expresión map tiene tipo Bool.
+ El programa while (true) {} no termina.
+ El resultado de evaluar (factorial 7) es 5040.
> En este contexto, las afirmaciones se llaman juicios.

## Sistemas deductivos

### Definición

Un sistema deductivo sirve para razonar acerca de juicios.
Está dado por reglas de inferencia, de la forma:

$$\dfrac{(premisa_1)(premisa_2)\dots premisa_n}{conclusión}\text{(Nombre de la regla)}$$

> Las reglas que no tienen premisas (n = 0) se llaman axiomas.

Las premisas son condiciones suficientes para la conclusión

+ **Lectura de arriba hacia abajo:**
si tenemos evidencia de que valen las premisas, podemos deducir que vale la conclusión.
+ **Lectura de abajo hacia arriba:**
si queremos demostrar que vale la conclusión, alcanza con demostrar que valen las premisas
### Derivación

Una **derivación** es un **árbol finito** formado por **reglas de inferencia**. Parte de ciertas premisas y llega a una **conclusión**.

Un **juicio** es **derivable** si **hay alguna derivación** sin **premisas** que lo **concluye**.
### Lógica proposicional

Las formulas son las expresiones que se pueden generar a partir de
la siguiente gramática:
```haskell
τ, σ, ρ, . . . ::= P | (τ ∧ σ) | (τ ⇒ σ) | (τ ∨ σ) | ⊥ | ¬τ
```
> La gramáticas definen sistemas deductivos de manera abreviada

> Una expresión τ se puede generar a partir de la gramática de arriba
si y sólo si el juicio `τ form` es derivable en el sistema de antes.

#### Convenciones de notación
+ Omitimos los paréntesis más externos de las formulas.
+ La implicación es asociativa a derecha.
	+ `τ ⇒ σ ⇒ ρ = (τ ⇒ (σ ⇒ ρ))`
+ los conectivos (∧, ∨) no son conmutativos ni asociativos

### Contexto:
Conjunto finito de formulas.
**Notación**: notamos con letras griegas mayúsculas $\{\Sigma,\Delta, \Gamma\}$   

### Deducción natural:

El sistema de deducción natural predica sobre juicios de la forma

$$\Gamma \vdash \tau$$
**Interpretación informal**: un juicio afirma que a partir de las hipótesis en el contexto $\Gamma$  es posible deducir la formula de la tesis

Hay 2 sistemas de deducción natural:
+ **Intuicionista**
+ **Clásica**

***Reglas de inferencia intuicionistas***:

|       | **Introducción**                                                                           | **Eliminación** |
| ----- | ------------------------------------------------------------------------------------------ | --------------- |
| **∧** | $\dfrac{\Sigma \vdash \tau, \Sigma \vdash \sigma}{\Sigma \vdash \tau \land \sigma}\land i$ |                 |
| **⇒** | $\dfrac{\Sigma, \tau \vdash \tau}{\Sigma \vdash \tau \rightarrow \sigma}\rightarrow i$     |                 |
| **∨** |                                                                                            |                 |
| **⊥** |                                                                                            |                 |
| **¬** |                                                                                            |                 |

**Reglas de inferencia clásicas**

Es como la intuicionista, pero con la regla del LEM incluida (no se puede deducir de las anteriores)

### Lógica intuicionista (NJ) vs lógica clásica (NK)

+ NK extiende a NJ con principios de razonamiento clásicos. Alcanza con agregar uno de ellos, por ejemplo ¬¬e .
+ Si un juicio es derivable en intuicionista, también es derivable en clásica.
	+ El contrarrecíproco no es válido
+ NJ es más restrictiva

> En la computación se suele usar más la intuicionista, pues permite razonar acerca de la **información**

Las **derivaciones NJ** se pueden entender como **programas**. Es la base de la **programación funcional**

## Semántica bivaluada

### Valuaciones
Una valuación es una función $v : P \rightarrow \{V, F\}$  que asigna valores de verdad a las variables proposicionales.

Una valuación v satisface una formula τ si v ⊨ τ , donde:
![[Pasted image 20250715155035.png]]

# TODO: pasarlo a markdown


### Corrección y completitud

Son equivalentes:
1. $\Gamma \vdash \tau$  es derivable en NK.
2. $\Gamma \vDash \tau$ 

La demostración está [[Demostración NK sii valuación]]
