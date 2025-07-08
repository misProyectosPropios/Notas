## Qué es?
Es una herramienta de orquestación open source creado por Google
Ayuda a manejar aplicaciones contenerizadas (containerized applications).

## Qué soluciona?

Se está pasando de monolitos a micro servicios, por lo que se están usando más contenedores. Por eso, se necesita una herramienta que logre manejar todos los contenedores adecuadamente

## Qué características proporciona?

+ Siempre es *accesible por los usuarios*;
+ *Escalable* y de *alto rendimiento*. Se ajusta bien en caso de aumentar el número de usuarios;
+ *Disaster recovery*: proporciona backups en caso de perdida de memoria y logra restaurarlo a la última versión

# Arquitectura

## Como funciona Kubernetes internamente

### Master node & worker nodes
> Node = maquina virtual o física
+ Tiene por lo menos un nodo maestro (master node)
+ Este nodo maestro tiene conecto varios "worker nodes"
	+ Estos nodos tienen un Kubelet process corriendo en ellos
	+ Cada uno de estos tiene varios contenedores de diferentes aplicaciones deployadas
	>En los worker nodes es donde la aplicación está corriendo
+ El nodo maestro no corre la aplicación, sino que corre Kubernetes processes que son indispensables para el funcionamiento del cluster
	+ **API server**: es el punto de entrada del cluster de Kubernetes. Va a recibir de UI, API o de Command Line  (CLI).
	+ **Controller Manager**: tiene un pantallazo de todo lo que ocurre en el cluster
	+ **Scheduler**: encargado de organizar y organizar los tiempos de los diferentes nodos según el workload y los recursos disponibles en cada nodo
	+ **ETCD**: key-value almacenamiento que guarda en todo momento el estado del Kubernetes cluster. Tiene info de los nodos. Sirve para los backups.
+ Los worker nodes son más grandes, tienen más carga y más recursos, pero el master node es más importante. Es necesario tener un backup de este

### Main components
+ Worker node (o node): physical or virtual machine 
+ Pod: es el componente más pequeño de Kubernetes
	+ Es una abstracción sobre un contenedor
	+ Solo corre una aplicación por Pod
	+ Para comunicarse entre ellos, tienen una dirección IP con la cual se comunican
	+ Son **efímeros**. Pueden morir fácilmente. Si mueren, se crea uno nuevo con una nueva dirección IP
+ **Service**: es una IP permanente. Sirve para que no cambien las direcciones IP de cada Pod cada vez que mueren
	+ **External service**: es una dirección IP abierta para todos
	+ **Internal service**: es una dirección IP que solo la pueden usar desde el cluster
+ **Ingress**: encargado de reenviar a cada service sus respectivos request

> Database URL deben de estar usualmente en el built application

### ConfigMap

Sirve para no tener que cuando hacemos un cambio de configuración tener que hacer too un trabajo repetitivo
Solo es para **data no confidencial**.
### Secret
Es como ConfigMap, pero es usado para guardar **información secreta**. Como contraseñas o credenciales.

### Volumes
Conecta un almacenamiento físico del disco al Pod. Puede estar en la misma máquina o afuera de Kubernetes
> Kubernetes no se encarga del data persistence

## Que pasa si se cae un Pod?

Como es un sistema distribuido, replicamos el mismo programa en varios servers, así evitamos que si se cae un Pod, no se caiga el programa por completo

Si tenemos duplicados los Pods, vamos a poder mandar cada request a alguno de ellos. A cual? Al menos ocupado. **Cómo lo hacemos?**: el service va a referenciar a todos los Pods y va a decidir a cual mandárselo.

#### Usamos el concepto de **[[Replication]]**

> Técnicamente no se replica, sino que se usa un blueprint para los Pods, donde se indican cuantas réplicas tenemos. Las réplicas no son Pods, sino que son [[Deployments]]

# Kubernetes Configuration

Ocurre en un nodo maestro al proceso API SERVER
+ Reciben una request el API SERVER desde UI, API o CLI con la configuración deseada
+ Dos formatos posibles:
	+ [[YAML]]
	+ [[JSON]]

## **[[Configuration]]**

## [[Minikube]]

## [[kubectl]]
