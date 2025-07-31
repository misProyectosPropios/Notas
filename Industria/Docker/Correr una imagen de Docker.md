Para correr una imagen de Docker:

```bash
docker run {name}:{tag} #Creates an container from a given image 
```

Al crear una imágen, le asigna un nombre automáticamente en caso de que no se específico alguno.

### Para terminar un container

Usar `ctrl + c` 

Si no podemos hacerlo con `ctrl + c` (porque `Detach`), podemos correr

```bash
docker stop {container} # Cierrra uno o más containers que están corriendo
```

### Si no existe el `{name}:{tag}`
Docker va a tratar de pullearlo de `Docker Hub`, lo va a pullear y lo va a correr
## Detach
```bash
docker run -d or (--detach) {name}:{tag} 
#Run container in background and prints its container ID
```

Si queremos ver sus logs, podemos hacer 

```bash
docker logs {container} #Views logs from service running inside the container
```

