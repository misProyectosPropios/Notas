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

## Sintaxis de tipos

```lambda
τ , σ, ρ, . . . ::= bool
				   | τ → σ
```

El conector **`->`** es **asociativo a derecha**

```lambda
τ → σ → ρ = τ → (σ → ρ)
```

Suponemos que tenemos un conjunto infinito numerable de variables
$$\chi = \{x,y,z\}$$
