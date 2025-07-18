Un programa en Prolog es una lista de cláusulas de definición.
Una consulta en Prolog es una clausula objetivo.

| Cláusulas | Prolog |
|---|---|
| $\{a(0, X, X)\}$ | `a(0,X,X).` |
| $\{a(s(X), Y, s(Z)), \neg a(X, Y, Z)\}$ | `a(s(X),Y,s(Z)) :- a(X,Y,Z).` |
| $\{\neg a(s(0), X, s(s(0)))\}$ | `?- a(s(0),X,s(s(0))).` |
> El orden y la multiplicidad son relevantes de las clausulas

### Criterio de selección: 
Elegir siempre el primer literal de la cláusula.

### Criterio de búsqueda:
Las reglas se usan en orden de aparición.
### No es **COMPLETO**
La exploración depth-first (**DFS**) es incompleta.
Para que sea completo, debería usar **BFS**

### Es **INCORRECTO**
Prolog no usa la regla occurs-check

`X unifica con f(X).` 

Puede provocar que Prolog encuentre una “refutación” incorrecta.

Ejemplo:

```prolog
esElSucesor(X, suc(X)).
?- esElSucesor(Y, Y).
✓ ...........................{Y := X, X := suc(X)}
```


Mencionar que no es completo
Mencionar que es falso también