 un sistema de distribución y almacenamiento de imágenes para correr ciertos programas, como `Redis`.

Acá hay imágenes oficiales de los programas.
Son mantenidas por los desarrolladores y por la comunidad de Docker

### **Docker Hub**

+ Es el más popular
+ Hay un grupo de gente especializado en Docker para publicar las imágenes 

>! Es práctica usar la mayoría de las veces una versión definida y no alguna en un rango

### **Importar de Docker**

Para importar de docker
```bash
docker pull {name}:{tag} #Pull an image from an registry
```

## Private vs public registries

+ Los que podes acceder  públicamente, sin registrarte, son **public**
+ Los que tenés que autenticarte antes de acceder a los registros son **private**

## Registry vs repository

+ Registry: 
	+ a service providing storage
	+ Can be hosted by a **third party** or by **yourself**
	+ Collection of repositories
+ Repository:
	+ Collection of related names but different versions

Básicamente, un Registry es una collección de repositorios. Y los repositorios son los que tienen las imágenes que nos interesan tanto