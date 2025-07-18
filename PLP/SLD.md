## Que es

Es un tipo de resolución, con algunas restricciones.
Es más rápida:
+ Resolución general:
	+ Búsqueda. Elegir dos cláusulas.
	+ Selección. Elegir un subconjunto de literales de cada cláusula.
+ Resolución SLD:
	+ **Menor generalidad:** solamente se puede aplicar sobre cláusulas de Horn
	+ **Mayor eficiencia**: opciones de búsqueda / selección reducidos

## Requisitos para poder usarla

### Definiciones

#### Cláusulas de Horn:
Las cláusulas son de los siguientes tipos, dependiendo del número
de literales positivos/negativos que contienen:

|                            | #positivos | #negativos |
| -------------------------- | ---------- | ---------- |
| cláusula **objetivo**      | 0          | \*         |
| cláusula de **definición** | 1          | \*         |
| cláusula de **Horn**       | $\leq 1$   | \*         |
Hay fórmulas que no se pueden escribir como cláusulas de Horn.

**Contraejemplo**
$$P \lor Q$$
#### Sustitución respuesta
Dada una refutación SLD, con pasos:
![[Pasted image 20250717205329.png]]

la sustitución respuesta es la composición $S_{n−1} \circ \dots \circ S_1$.
## Características

+ Involucra siempre a una cláusula de definición y una cláusula objetivo
+ La selección es binaria (un literal de cada clausula).
+ La resolvente es una nueva cláusula objetivo.
+ Es una resolución lineal
+ Una derivación SLD comienza con n ≥ 0 cláusulas de definición y una cláusula objetivo

En cada paso:
+ Se elige una cláusula definición$ $D_j$ con 1 ≤ j ≤ n.
+ Se aplica la regla de resolución SLD sobre $D_j$ y $G_i$ .
+ La resolvente es una nueva cláusula objetivo $G_{i+1}$.

+ Es de la forma:
![[Pasted image 20250717204850.png]]

+ La b´usqueda se simplifica.
	+ Se limita a elegir Ci como una de las n cláusulas $D_1, \dots ,D_n$.
	  La cláusula objetivo Gi está fijada, no hay alternativas.
+ La selección se simplifica.
	+ Se limita a elegir uno de los literales negativos de Gi .
	  La cláusula de definición Ci tiene un único literal positivo

## Completitud del método de resolución de SLD
El método de resolución es completo para cláusulas de Horn.
### Teorema

Más precisamente,  si $D_1, \dots ,D_n$ son cláusulas de definición y G
una cláusula objetivo:

+ Si $\{D_1, \dots ,D_n\}$ es insatisfactible, existe una refutación SLD.
+ Si tenemos alguna clausula que no sea de Horn puede existir una resolución SLD o no, dependiendo si se puede probar con el subconjunto que sea cláusulas de Horn



## Relación SLD <-> Prolog

[[Relación SLD con Prolog]]