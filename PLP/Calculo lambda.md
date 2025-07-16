## Definición y usos
**Definición:** Lenguaje de programación definido de manera rigurosa.
Se basa solo en dos **operaciones**: **construir funciones y aplicarlas.**

### Historia:
+ Creado en 1930 por Church para formalizar la noción de función efectivamente computable
+ Usado en 1960 para estudiar la semántica formal de lenguajes de programación
### Actualmente
+ Núcleo de lenguajes de programación funcionales y asistentes de demostración.
  Lisp, OCaml, Haskell, Coq, Agda, Lean, . . ..
+ Laboratorio para investigar nuevas características de lenguajes.
+ Fuertemente conectado con la teoría de la demostración, matemática constructiva, teoría de categorías, . . .

## Sintaxis

### Sintaxis de los tipos

```lambda
τ , σ, ρ, . . . ::= bool
				   | τ → σ
```

El conector **`->`** es **asociativo a derecha**

```lambda
τ → σ → ρ = τ → (σ → ρ)
```

### Sintaxis de los términos

Suponemos que tenemos un conjunto infinito numerable de variables
$$\chi = \{x,y,z\}$$
```haskell
M,N, P, . . . ::= x                    variable
				| λx : τ .M            abstracción
				| M N                  aplicación
				| true                 verdadero 
				| false                falso
				| if M thenN else P    condicional
```


#### Notación
Asumimos que la aplicación es asociativa a izquierda:
```haskell
M N P = (M N) P
```

La abstracción y el “if” tienen menor precedencia que la aplicación:
```haskell
λx : τ.M N = λx : τ. (M N)
```

### Variables libres y ligadas
+ Una ocurrencia de x está **ligada** si aparece adentro de una abstracción “λ x”.
+ Una ocurrencia está **libre** si **no es ligada**

### Alfa equivalencia

Los términos que difieren sólo en el nombre de variables ligadas se consideran iguales:

### Sistemas de tipos

La noción de “tipabilidad” se formaliza con un sistema deductivo.
> Resuelve el problema de ¿Qué tipo tiene x?

#### Contexto de tipado
Un **contexto de tipado** es un **conjunto finito de pares** (xi : τi ):
$$\{x_1:\tau_1, \dots, x_n:\tau_n\}$$

sin variables repetidas $(i \neq j \Rightarrow x_i \neq x_j )$. 

A veces notamos $dom(\Gamma) = \{x_1, \dots , x_n\}$.

El sistema de tipos predica sobre juicios de tipado, de la forma
$$ \Gamma \vdash M : \tau$$
### Reglas de tipado

![[Pasted image 20250715193228.png]]
# TODO pasarlo a latex

### Teorema (Unicidad de tipos)
Si Γ ⊢ M : τ y Γ ⊢ M : σ son derivables, entonces τ = σ.
### Teorema (Weakening + Strengthening)
Si $\Gamma \vdash M:\tau$  es derivable y $fv(M) \subseteq dom(\Gamma \cap \Gamma′)$ entonces
$\Gamma' \vdash M:\tau$ es derivable.

## Cálculo-$\lambda^b$ : semántica operacional
El sistema de tipos indica cómo se construyen los programas. 
Queremos además darles significado (semántica).

Distintas maneras de dar semántica formal
1. **Semántica operacional.**
   Indica cómo se ejecuta el programa hasta llegar a un resultado.
   Semántica small-step: ejecución paso a paso.
   Semántica big-step: Evaluación directa al resultado
2. **Semántica denotacional**
   Interpreta los programas como objetos matemáticos.
3. Semántica axiomática.
   Establece relaciones lógicas entre el estado del programa antes y después de la ejecución.
4. etc.

### Small-step
#### Programa
Un programa es un término M tipable y cerrado $(fv(M) = \emptyset)$
+ El juicio de tipado $\vdash M : \tau$ debe ser derivable para algún $\tau$ .
#### Juicios de evaluación
La semántica operacional predica sobre juicios de evaluación:
$$M \rightarrow N$$
donde M y N son programas

#### Valores
Los valores son los posibles resultados de evaluar programas:

```haskell
V ::= true | false | λx : τ.M
```


![[Pasted image 20250715195044.png]]

![[Pasted image 20250715195057.png]]

#### Sustitución

La operación de sustitución:
$$M{x := N}$$
denota el término que resulta de reemplazar todas las ocurrencias libres de x en M por N.

![[Pasted image 20250715195147.png]]

# TODO: pasar todas las imagenes a latex

![[Pasted image 20250715195214.png]]




![[Pasted image 20250715195243.png]]


![[Pasted image 20250715195252.png]]


## Extensión de números naturales:

### Sintaxis: tipos
```haskell
τ , σ, . . . ::= . . . | nat
```

### Sintaxis: términos

```haskell
M ::= . . .
	| zero              el número cero
	| succ(M)           el sucesor del número que representa M
	| pred(M)           el predecesor del número que representa M
	| isZero(M)         representa un booleano true/false,
				        dependiendo de si M representa al cero o no
```

![[Pasted image 20250715195521.png]]


### Valores

```haskell
V ::= . . . | zero | succ(V)
```

![[Pasted image 20250715195554.png]]


#### Forma normal (“f.n.”)
Un programa M es una f.n. si no existe M′ tal que M → M′.