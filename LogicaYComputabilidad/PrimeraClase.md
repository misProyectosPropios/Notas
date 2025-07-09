	2 temas: lógica y computabilidad

Computabilidad:
+ Es el estudio de los métodos efectivos, de procedimientos automáticos.
  Trata de estudiar lo que no pueden computar las máquinas por la naturaleza de los problemas no resolubles
Lógica:
+ Proposicional: sobre propiedades y como conectar propiedades con conectores booleanos
+ Primer orden: Distinción entre elementos y sus propiedades
	+ Con cuantificadores existenciales y universales

## Bibliografía

+ Computabilidad: "Computability, Complexity and Languages, fundamentals of theoretical computer science. Martin Davis, Ron Sigal, Elaine Weyuker, Elsevier, 1994";
+ Proposicional: "Metalógica, introducción a la metateoría de la lógica clásica de primer orden. Geoffrey Hunter, Editorial Paraninfo, 1981";
+ Primer orden: "A mathematical introduction to logic. Herbert Enderton, Elsevier, 2006".

## Empieza clase

Formalizaciones:
+ Máquina de Turing

Orígenes: 
Hilbert tenía interés por fundamentos de la matemática

Quería formalizarla:
+ Completitud de la aritmética
	+ Sistema axiomático que capturara las verdades de la aritmética
	+ Gödel: cualquier sistema axiomático suficientemente poderoso es incompleto o inconsistente
+ Problema de decisión
	+ decidir si cualquier fórmula de primer orden es válida o no
	+ Turing: no existe tal procedimiento efectivo

Ambas son falsas, no son completas.

Pero, que es una máquina de Turing?
--------------------------------------------
Es una cinta de tamaño infinito que está dividida en celdas. Cada celda puede tener una cantidad finita de símbolos. Hay una cabeza que puede escribir o leer, pero de una sola celda a la vez. La cabeza está solamente en una cantidad finita de estados

+ La máquina tiene un alfabeto $\Sigma$ que tiene al $*\in\Sigma$ siempre.
	+ Definimos \* como una celda vacía
+ La cabeza:
	+ lee y escribe símbolos en una celda a la vez
	+ Se mueve solamente una posición a la izquierda o a la derecha a la vez.
+ L y R serán acciones sobre la cabeza, no están en el alfabeto
+ Estás maquinas son programables
	+ Tiene una tabla finita de instrucciones que dice que hacer en cada paso

Tabla de instrucciones:
+ $\Sigma$ es el alfabeto. $L,R\notin \Sigma \land *\in\Sigma$ 
+ Q es el conjunto finito de estados (son los estados de las instrucciones del programa)
+ A = $\Sigma \cup \{L,R\}$ 
+ Un símbolo $s \in \Sigma$ se interpreta como escribir s en la posición de la cabeza
+ L: mover a la izquierda
+ R: mover a la derecha
+ T (tabla de instrucciones) es un subconjunto finito de: Q x  $\Sigma$ x A x Q

Si tenemos la tupla (Q, $\Sigma$, A, Q') $\in T$  interpreta: 
> Si la máquina está en el estado q leyendo en la cinta el símbolo s, entonces realiza la acción a y pasa al estado q'

### **Definición**

Una máquina de Turing es una tupla
$$ (\Sigma;Q;T; q_{0}; q_{f})$$
donde 
+ $\Sigma$ es finito
+ Q (finito) es el conjunto de estados
	+ Tiene 2 estados distinguidos
		+ $Q_{0} \in Q$ es el estado inicial
		+ $Q_{f} \in Q$ es el estado final
+ $T \subseteq Q \texttimes \Sigma \texttimes \Sigma \cup \{L,R\} \texttimes Q$ es la tabla de instrucciones
	+ Es finita (pues $\Sigma$ y $Q$ son ambas finitas)

### **Clasificación**:
+ Cuando no hay restricciones sobre T decimos que **$\mathcal{M}$  es una máquina de Turing no determinística**
+ cuando no hay dos instrucciones en T que empiezan con las mismas primeras dos coordenadas, decimos que **$\mathcal{M}$ es una máquina de Turing determinística**

### **Definición**: 
Autómata: es un grafo que tiene etiquetas en los nodos y las flechas y sirve para entender las tablas de instrucciones de una máquina de Turing


### **Representación de números en máquinas de Turing**

Los números los podemos representar en la base unaria $\Sigma = \{*,1\}$, donde
+ 0 = 1
+ 1 = 1,1
+ Y así sucesivamente al números $X$ como $\overline{X} = 1..1 ((X + 1) 1s)$ 

### **Funciones parciales**

Vamos a trabajar con funciones $X^{n}\rightarrow X$ , pero no van a estar definidas para todas las entradas. Pueden estar indefinidas para un valor $(x_{1},x_{2},\dots,x_{n})$  o para varios o para ninguno.

**Notación**
+ $f(x_{1},x_{2},\dots,x_{n}) \downarrow$ si está _**definida**_ para ese valor
+ $f(x_{1},x_{2},\dots,x_{n}) \uparrow$ si está _**indefinido**_ para ese valor

**Definición:**
_Dominio_: es el conjunto ded valores para los cuales está definida la función
$$ dom(f) = \{(x_{1}, \dots,x_{n} : f(x_{1},\dots,x_{n}) \downarrow) \}$$
$f$ es total si $dom(f) = \mathbb{N}^{n}$


## Función Turing computable

Una función es **Turing computable** si $\exists$ maquina de Turing determinística con $\Sigma = \{*,1\}$  tal que cuando empieza la configuración inicial![[Pasted image 20250707110247.png]]

con los enteros $X_{i}$ representados en unario y nada más en la entrada
Entonces
+ si $f(x_{1},x_{2},\dots,x_{n}) \downarrow$, entonces siguiendo las instrucciones en T llega a una configuración final de la forma ![[Pasted image 20250707110436.png]]
+ Si $f(x_{1},x_{2},\dots,x_{n}) \uparrow$ entonces nunca termina en el estado $Q_{f}$

_Ejemplo de función parcial:_

$$f(x)=\begin{cases}
x & \text{si } x \text{ es par} \\
\uparrow & \text{si no}
\end{cases}$$

### **Poder del cómputo**

**Teorema**:
Sea $f : \mathbb{N}^{m} \rightarrow \mathbb{N}$ una función parcial. Es equivalente:
+ $f$ es computable en Java;
+ $f$ es computable en C;
+ $f$ es computable en Haskell;
+ $f$ es Turing computable;
**No es importante**:
+ Que base usamos para representar números
+ Si permitimos que la cinta tenga otras cosas escritas además de la salida o solo contenga la salida
+ si usamos esta variante de arquitectura:
	+ una cinta de entrada (solo de lectura)
	+ una cinta de salida (solo de escritura)
	+ una o varias cintas de trabajo, de lectura/escritura

### [[SegundaClase]]
