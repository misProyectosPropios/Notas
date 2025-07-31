
```bash
docker run -d or (--detach) {name}:{tag} 
#Run container in background and prints its container ID
```

```bash
docker run --name {nombre_en_una_palabra} -d -p {host}:{container} {name}:{tag}
# Le asigna un nombre al docker y no el automático
```