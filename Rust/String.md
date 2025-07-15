Hay 2 tipos:
+ Literal: hardcodeada en el código. Rápidas y eficientes. Inmutables
+ String type: alocada en el [[Heap]]. No se sabe en tiempo de compilación su tamaño.
Es mutable. Más lenta que los literales.

En el Rust, si queremos copiar el contenido, pero no queremos jodernos con el [[Ownership]], se puede usar 

```rust
let s1 = String::from("hello");
let s2 = s1.clone();
```
