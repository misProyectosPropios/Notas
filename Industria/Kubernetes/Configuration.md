Para la configuración, hay 3 partes:
1. **Metadata**:
	1. *Name*:
2. **Specification**:
	1. *Kind*: Deployment, Service,
	2. *ApiVersion*:
	3. *spec*: dependen del tipo del Kind
3. **status**: no lo hacemos nosotros en la configuración, sino que lo hace y edita automáticamente Kubernetes.
	1. Compara cual es el *desired state* y cual es el *actual state*. Si no son iguales, Kubernetes va a tratar de arreglar lo que se rompió.
	2. La info, con la que compara, la trae del ETCD, que este en el nodo maestro.
	3. 