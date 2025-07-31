Hay 2 cortes:
+ Green Cut
	+ No altera la semántica del programa
	+ Genera programas más eficientes
+ Red Cut:
	+ La semántica se ve alterada

## Predicado !

Tiene **éxito** inmediatamente
### Uso
Al momento de hacer backtracking:
+ Se vuelve atrás hasta el punto en el que se eligi´o usar la regla que hizo aparecer el operador de corte.
+ Se descartan todas las elecciones alternativas
+ Se continúa buscando hacia atrás.
## Negación por falla:

### not:
Si fail es un predicado que falla siempre, se puede definir la
negación en Prolog asi:

```prolog
not(P) :- P, !, fail.
not(P).
```

> Observación. not(P) tiene éxito si y sólo si P falla.
### Características:
+ El orden de los literales en la consulta se vuelve relevante.
  Esto atenta contra la declaratividad.