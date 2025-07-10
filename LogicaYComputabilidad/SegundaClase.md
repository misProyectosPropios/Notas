
Otra manera de formalizar **función calculable de manera efectiva**:
+ Empezamos por funciones simples, efectivas intuitivamente
+ Si las mezclamos de alguna manera efectiva, dos o más funciones que ya eran efectivas van a seguir siendo efectivas

### **Definiciones de funciones iniciales**:
+ $S(X) = x+1$
+ $n(X) = 0$
+ *Proyecciones*: $u^{n}(X_{1},\dots, X_{n}) = X_{i}$ para $i\in\{1,\dots, n\}$ 

### **Definición de composición**:

Sea $f:\mathbb{N}^k \rightarrow \mathbb{N}$ y $g_1, \dots, g_k : \mathbb{N}^{n} \rightarrow \mathbb{N}$.
$h: \mathbb{N}^{n} \rightarrow \mathbb{N}$ se obtiene a partir de f y $g_1, \dots g_k$ por **composición** si

$$h(x_{1}, \dots, x_{n}) = f(g_1(x_1, \dots, x_n), \dots, g_k(x_1, \dots, x_n))$$
### **Definición de recursión primitiva**:

$h: \mathbb{N}^{n+1} \rightarrow \mathbb{N}$ se obtiene a partir de $g:\mathbb{N}^{n+2}\rightarrow{N}$ y $f:\mathbb{N}^{n}\rightarrow{N}$ por **recursión primitiva** si
$$\begin{align*}
h(x_{1}, \dots, x_{n}, 0) &= f(x_{1}, \dots, x_{n}) \\
h(x_{1}, \dots, x_{n}, t+1) &= g(h(x_{1}, \dots, x_{n}, t), x_{1}, \dots, x_{n}, t)
\end{align*}$$

> Si n=0 en $x_{1},\dots, x_{n}$, entonces, lo podemos considerar a $f(x_{1},\dots, x_{n})$ como una constante $\in \mathbb{N}$

 