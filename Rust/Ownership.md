
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

#### Propiedades:
+ Al pasar un objeto a una función, el objeto se manda a la función y no podemos usar más la variable.
+ Al devolver un objeto, la función receptora, puede usar esa objeto ahora
	+ Entonces, podríamos pasar un objeto y al devolver la función, devolverlo como una tupla de los objetos recibidos y el resultado per se. 
	+ Otra solución: **referencias**
##### Referencia
+ Para pasar una referencia:
	+ Usar `&variable` 
	+ Pasar una referencia a un puntero de la variable.
	+ La variable que manda no se vuelve dueña de la variable.
	+ Las referencias **por default** son inmutables
		+ Para hacerlas mutables, usar ``&mut variable`` 

Ejemplo de uso:

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{s1}' is {len}.");
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```
![[Pasted image 20250712111347.png]]

Esta característica de Rust sirve para evitar **data race**:
- Two or more pointers access the same data at the same time.
- At least one of the pointers is being used to write to the data.
- There’s no mechanism being used to synchronize access to the data.

> Las referencias pueden tener:
> 	Una referencia mutable
> 	 Infinitas referencia inmutables
> Pero no pueden tener:
> 	2 o más referencias mutables
> 		Referencias mutables e inmutables al mismo tiempo

