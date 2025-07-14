Son un conjunto de **keys** con un valor asociado (como un diccionario). Se le asigna a cada nombre un valor

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```

Para crear un struct:

```rust
let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
```

Para acceder a los valores de un struct:

```rust
struct_nombre.key;
```

Para modificar el valor de una key:

```rust
struct_nombre.key = new_value;
```

### Sintax sugar:

Si queremos crear un struct usando los valores instanciados en otro struct, podemos usar:

```rust
let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
```

que va a poner el mail como el que inicializa, pero después va a asignarle a todo el resto los mismo valores que user1.

## Structs as tuples

Se pueden crear structs **sin keys**. 
```rust
struct Point(i32, i32, i32);
```
Sirve para diferenciar una tupla e algo más específico, en este caso, puede ser un RGB por ejemplo


## Unit type

Solamente quiero tener un valor para guardar
```rust
struct AlwaysEqual;
```