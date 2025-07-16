
**Máquinas virtuales**
Tiene 3 partes:
1. OS Application Layer
2. OS Kernel
3. Hardware
Cuando se hace una máquina virtual se crean la 1. y la 2.
### Como hace Docker para correr los containers?

Docker aprovecha el Kernel del Host y virtualiza la parte de OS Application Layer, haciéndolo más rápido por ese motivo también 

## Ventajas de Docker sobre las máquinas virtuales

+ Imágenes de Docker más pequeñas que de una OS (MB contra GB)
+ Docker es mucho más rápido que una VM
+ Las VM son compatibles con todos los sistemas operativos, mientras que Docker solamente con Linux
	+ Aunque existe Docker Desktop que permite correr Docker containers de Linux en Windows o Mac