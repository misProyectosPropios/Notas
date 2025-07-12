La función `main` es la que se llama cuando se ejecuta un programa en Rust

fn nombre_funcion() {

}

> Notación: Cuando se cree un archivo de Rust de varias palabras, usar la notación "palabra_palabra" 

**Sintaxis: !**: el `!` sirve para llamar a funciones especiales:  **macros**

**println!**: muestra en pantalla el texto pasado

### Rust:
 Es un lenguaje compilado. Hay que correr
 ```bash
 rustc main.rs
 .\main # or ./main si no fuese windows
```

Además, tiene un tipo fuerte estático de variables.
Y tiene inferencia de tipos
#### **Cargo**
Para manejar los proyectos haciéndolos más complejos, se usa **Cargo**. Sirve para compartir el código entre varios, estandarizar directorios y correr el código más fácil.

Genera un proyecto en la subcarpeta con el nombre del proyecto
```bash
cargo new nombre_proyecto
```


Genera el ejecutable en `target/debug`
```bash
# En el directorio con el .toml, correr el siguiente código
cargo build
.\target\debug\hello_cargo # or ./target/debug/hello_cargo si no fuese Windows
```


O para hacerlo todo en una linea:

```bash
cargo run
```

Y también para checkear que compile el código, tiene el comando:
```
cargo check
```

Para publicar un **release**, se ejecuta:
```
cargo build --release
```
que genera un ejecutable con optimizaciones.
Genera el ejecutable en `target/release`


## Variables en Rust

Las variables en Rust son inmutables default. 
Para hacerla mutable a la variable, tenemos que agregar el `mut` antes de la creación de la variable

Ejemplo:
```rust
let apples = 5; // immutable
let mut bananas = 5; // mutable
```

> Para hacer comentarios en Rust:
> 	**//** : comentarios de una linea
> 	/* */ , / \*! \*/ o /// //!
 	
En Rust, el `println!` para mostrar variables en medio de un string se hace así:
```rust
println!("Texto {variable} más texto");
```

### **Dependencies**:

Si se quiere agregar una dependencia:
```toml
[dependencies]
rand = "0.8.5" # Siendo 0.8.5 la versión de la dependencia
```

Si corremos `cargo build`, va a descargar todas las dependencias

Si lo corremos nuevamente, ya estarán instaladas, por lo que no va a descargar ninguna.

Si quisiéramos actualizar y buscar si hay una nueva versión que satisfaga nuestras especificaciones del archivo `.toml`, entonces se debería correr:
```toml
cargo update
```

Para obtener números random (o pseudo random):
```
rand::thread_rng().gen_range(1..=100);
```


## Rust variables

Para comparar números:
```rust
match guess.cmp(&number) {
	Ordering::Less => println!("Too small!"),
    Ordering::Greater => println!("Too big!"),
    Ordering::Equal => println!("You win!"),
    }
}
```

Pero, number tiene que ser de tipo númerico para funcionar

