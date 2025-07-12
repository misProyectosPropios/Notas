Para hacer loops en Rust:

```rust
loop {
 //código
}
```

Este código de arriba sería como un `while true`

Para salir de un `loop` se puede usar un **`break`**

Bucle condicional:
```rust
while condition {
	code
}
```

**`for each`**
```rust
for element in collection {
	code
}
```

Para hacer un bucle durante cierto tiempo:

```rust
for number in (1..4).rev() {
        println!("{number}!");
    }
```
