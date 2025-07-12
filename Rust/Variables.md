Las variables son inmutables por defecto
Para hacerlas mutables, solamente hace falta agregar el `mut` al principio cuando se declara la variable

## Constante

Para declarar una constante:
```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

## Shadowing

En Rust, podemos declarar 2 veces una variable con distinto nombre. Esto se llama Shadowing. Sería como una _"sobre escritura"_ del nombre de la variable

## Mut

Las variables son inmutables, excepto cuando las usamos con *mut*. Esto significa que podemos asignarle nuevos valores _**del mismo tipo**_. No podemos cambiar el tipo de la variable si le asignamos un valor.