
We want to deploy our app as Docker Container
## Solution: `Dockerfile`

It's a text document that contains commands to assemble an image

Docker can then build an image by reading those instructions

> Es una especificación de lo que necesita el proyecto para funcionar y después que usar de este

Empiezan de una **parent image**

Es una Docker image en la cual tu imagen esta basada

```Dockerfile
FROM {name}:{tag}
COPY {file} {to where} (/app/) the slash at the end indicates to create a NEW folder in case that /app is not a folder
RUN {command}

CMD
```

Definiciones:
+ `FROM`  Build this image from the specified image
+ `RUN` Will execute any command in a shell inside the `container image`
+ `COPY` files or directories from `<src>` and adds them to the file-system of the container at the path `<dest>`
	+ It's executed on the host
+ `WORKDIR` sets the working for all following commands
	+ Like changing the `cd`
+ `CMD` The instruction that  is to be  executed when a Docker container starts
	+ Solo puede haber uno en cada `Dockerfile`
	+ `CMD ["executable", "param1", ..., "paramN"]`

### Crearla finalmente

```bash
docker build {path} # Creates a Docker image from a Dockerfile
```

+ `-t / --tag:`
	+ Sets a name and optionally a tag in the `name:tag` format
+ `{path}`:
	+ Una típica puede ser el `.`, refiriendose al `current directory`
+ 