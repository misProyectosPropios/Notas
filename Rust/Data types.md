Todos los valores de Rust tienen un tipo de dato que le indican a Rust que operaciones se puede hacer en ese tipo de dato.

####  _statically typed_ language
Tiene que saber en tiempo de compilación que tipo es cada una de las variables.

## Scalar types

Representan un único valor.
+ Integer:

|   |   |   |
|---|---|---|
|8-bit|`i8`|`u8`|
|16-bit|`i16`|`u16`|
|32-bit|`i32`|`u32`|
|64-bit|`i64`|`u64`|
|128-bit|`i128`|`u128`|
|arch|`isize`|`usize`|

| Number literals  | Example       |
| ---------------- | ------------- |
| Decimal          | `98_222`      |
| Hex              | `0xff`        |
| Octal            | `0o77`        |
| Binary           | `0b1111_0000` |
| Byte (`u8` only) | `b'A'`        |
Si ocurre overflow al hacer una operación sobre enteros, pueden ocurrir diferentes cosas:
+ Debug: suelta una alerta de **`panic`**  
+ Release: hace un resto de la cuenta.

+ Floating-point
	+ `f32`
	+ `f64`
+ Booleanos
	+ bool
		+ true
		+ false
+ Characters
	+ char

#### Compound types

##### Tup
tup: (tipo, $\dots$, tipo) = (valor, $\dots$, valor)

Para acceder a cada posición: 
```rust
x.i // siendo i un número del 0 al length de x - 1 incluido
```

##### Array

Todos los elementos son del mismo tipo
Estas son las formas de crearlos

```rust
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
```

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

```rust
let a = [3; 5];
```

Para acceder a los elementos:

```rust
let a = [1, 2, 3, 4, 5];
let first = a[0];
```
