Docker abre un puerto pero no es de localhost. Ese es el `container port`

Para unir un puerto del **localhost** con los `container port`, lo hacemos al correr un container

```bash
docker run -p {host_port}:{container_port} {name}:{tag} 
# Muestra el host_port relacionandolo con el container_port
```

> Solo 1 service puede estar corriendo en un puerto del host especificado

> Standard: se suele usar el mismo puerto en el host y en el container

