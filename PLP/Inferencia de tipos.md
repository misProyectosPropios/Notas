## Introducción

### Notación

#### Términos sin anotaciones de tipos:

```
U ::= x | λx.U | U U | True | False | if U then U else U
```
#### Términos con anotaciones de tipos:

```
M ::= x | λx : τ.M | M M | True | False | if M then M else M
```

#### Erase(M):

erase(M) al término sin anotaciones de tipos que resulta de borrar las anotaciones de tipos de M.
### Definición del problema de inferencia de tipo
#### Tipable
Un término U sin anotaciones de tipos es tipable sii existen:
+ un contexto de tipado $\Gamma$
+ un término con anotaciones de tipos M
+ un tipo $\tau$
tales que erase(M) = U y Γ ⊢ M : τ .

#### Problema de inferencia de tipos

Dado un término U, determinar si es tipable.
+ En caso de que U sea tipable:
	+ hallar un contexto $\Gamma$, un término M y un tipo $\tau$ tales que $erase(M) = U \land \Gamma \vdash M : \tau$ .
### Algoritmo 

## Algoritmo de unificación

> El algoritmo se basa en manipular tipos parcialmente conocidos

> Incorporamos incógnitas $(X_1, X_2, X_3, \dots)$ a los tipos.
### Suposiciones
Fijado un conjunto finito de constructores de tipos:
+ Tipos constantes: Bool, Int, . . ..
+ Constructores unarios: (List •), (Maybe •), . . ..
+ Constructores binarios: (• → •), (• × •), (Either • •), . . ..
+ (Etcétera).
### Definiciones

#### Tipos:
$$\tau ::= X_n \text{ | } C(\tau_1, \dots , \tau_n)$$
#### Unificación
Es el problema de resolver sistemas de ecuaciones entre tipos con incógnitas.
#### Sustitución
Es una función que a cada incógnita le asocia un tipo.

**Notación**

$$S = \{X_{k_1} := \tau_1, \dots , X_{k_n} := \tau_n\}$$
tal que $S(X_{K_i} = \tau_i) \text{ } \forall \text{ }1 \leq i \leq n$   y $S(X_k) = X_k$ para todas las otras incógnitas

Si $\tau$ es un tipo, escribimos $S(\tau)$ para el resultado de reemplazar cada incógnita de $\tau$ por el valor que le otorga S.

#### Problema de unificación
Un problema de unificación es un conjunto finito E de ecuaciones entre tipos que pueden involucrar incógnitas
$$E = \left\{ \tau_1 \stackrel{?}{=} \sigma_1,\, \tau_2 \stackrel{?}{=} \sigma_2,\, \dots,\, \tau_n \stackrel{?}{=} \sigma_n \right\}$$


#### Unificador
Un unificador para E es una sustitución S tal que:
$S(\tau_1) = S(\sigma_1)$
$S(\tau_2) = S(\sigma_2)$
$\dots$ 
$S(\tau_n) = S(\sigma_n):$

#### Sustitución más general

Una sustitución $S_A$ es más general que una sustitución SB si existe una sustitución SC tal que:

$$ S_B = Sc \circ S_A$$

> $S_B$ se obtiene instanciando variables de $S_A$

**Notación**: mgu(E) al unificador más general de E
### Algoritmo de unificación de Martelli–Montanari

Dado un problema de unificación E (conjunto de ecuaciones):
+ Mientras E ̸= ∅, se aplica sucesivamente alguna de las seis reglas que se detallan más adelante.
+ La regla puede resultar en una falla.
+ De lo contrario, la regla es de la forma $E \rightarrow_S E′$  . 
  La resolución del problema E se reduce a resolver otro problema E′, aplicando la sustitución S.

Hay dos posibilidades:
1. $E = E_0 \rightarrow_{S_1} E_1 \rightarrow_{S_2} E_2 \rightarrow \dots \rightarrow{S_n} E_n \rightarrow_{S_{n+1}} \text{falla}$    
En tal caso el problema de unificaci´on E no tiene solución.
2. $E = E_0 \rightarrow_{S_1} E_1 \rightarrow_{S_2} E_2 \rightarrow \dots \rightarrow{S_n} E_n = \emptyset$ 
En tal caso el problema de unificación E tiene solución.

### Casos

![[Pasted image 20250716111838.png]]
### Demostración de correctitud del algoritmo

### Terminación del algoritmo de unificación


## Algoritmo de inferencia de tipos (Algoritmo $\mathcal{I}$ )

### Pasos

#### Rectificación
Decimos que un término esta **rectificado** si:
1. No hay dos variables ligadas con el mismo nombre.
2. No hay una variable ligada con el mismo nombre que una variable libre.

> Siempre se puede rectificar un terminó α-renombrándolo.
#### Anotación

Tenemos un término U, que suponemos ya rectificado.

Producimos un contexto $\Gamma_0$ y un término $M_0$:
1. El contexto $\Gamma_0$  le da tipo a todas las variables libres de U. 
   El tipo de cada variable es una incógnita fresca.
2. El término $M_0$ está anotado de tal modo que $erase(M_0) = U.$
   Todas las anotaciones son incógnitas frescas.
#### Generación de restricciones

Tenemos un contexto $\Gamma$ y un término M con anotaciones de tipos.
**Recursivamente** calculamos:
1. Un tipo τ , que corresponde al tipo de M.
2. Un conjunto de ecuaciones E.
   Representan restricciones para que M esté bien tipado.
$$\mathcal{I}
\left(
\underbrace{
    \underbrace{\Gamma}_{\text{contexto}}
    \mid
    \underbrace{M}_{\text{término}}
}_{\text{entrada}}
\right)
=
\left(
\underbrace{\tau}_{\text{tipo}}
\mid
\underbrace{E}_{\text{restricciones}}
\right)_{\text{salida}}
$$


con la precondición de que Γ le da tipo a todas las variables de M.
#### Unificación de las restricciones

Una vez calculado $\mathcal{I}(\Gamma_0 \text{ | }  M_0) = (\tau \text{ | } E)$:
1. Calculamos $S = mgu(E)$.
2. Si no existe el unificador, el término U no es tipable.
3. Si existe el unificador, el término U es tipable y vale:
$$S(\Gamma_0) \vdash S(M_0) : S(\tau )$$
### Correctitud del algoritmo


## Corrección del algoritmo de unificación

