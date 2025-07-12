
Reglas
+ Cada valor en Rust tiene un **owner**
+ Solo hay un dueño en cada momento del programa
+ Cuando el **owner** esta fuera del scope, el valor será **borrado** (_dropped_)

[[String]]

Es un ejemplo de objeto guardado en el heap. 
No usa un Garbage collector, sino que use el **[[Ownership]]** para liberar memoria.
Siempre que una variable se va fuera de scope, llama a **drop** que la borra de la memoria.

Si hacemos 
```rust
let s1 = String::from("hello");
let s2 = s1;
println!("{s1}, world!");
```

va a generar un error, pues el s1 es borrado como variable para asignar que el nuevo padre sea `s2`.


> Si tenemos una variable que no es un puntero, como un `Int`, entonces no va a generarse problemas en ese caso.

##### Al pasar un objeto a una función, el objeto se manda al 

