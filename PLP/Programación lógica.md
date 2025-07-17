**Ideal de la programación declarativa**
Los programas deberían asemejarse a especificaciones.

#### Funcionamiento
+ El usuario escribe una fórmula
+ El sistema busca satisfacer o refutar la fórmula
	+ En caso de lograr satisfacerla, el sistema produce una salida que verifica la propiedad P buscada.

## Prolog

Prolog opera con términos de primer orden:

Las fórmulas atómicas son de la forma $pred(t_1, \dots , t_n)$
#### Programa
Un programa es un conjunto de reglas. Cada regla es de la forma

$$\sigma \text{ :- } \tau_1, \dots , \tau_n.$$

Las reglas en las que n = 0 se llaman **hechos** y se escriben:
$$ nombre(\text{param}_1, \dots, \text{param}_n)$$

Las reglas tienen la siguiente interpretación lógica

$$
\forall X_1 \dots \forall X_k.\, ((\tau_1 \land \dots \land \tau_n) \Rightarrow \sigma)
$$
#### Consulta
Una consulta es de la forma:
$$
\ ?{-}\sigma_1,\, \dots,\, \sigma_n
$$

Las consultas tienen la siguiente interpretación lógica:
$$
\exists \mathbf{X}_1 \dots \exists \mathbf{X}_k.\, (\sigma_1 \land \dots \land \sigma_n)
$$

donde $X_1, \dots , X_k$ son todas las variables libres de las fórmulas.

+ El entorno de Prolog busca demostrar la fórmula τ de la consulta.
+ En realidad busca refutar ¬τ , o sea, demostrar ¬τ ⇒ ⊥
+ La búsqueda de la refutación se basa en el metodo de resolución