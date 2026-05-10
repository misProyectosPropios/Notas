Dos focos
Principios de ciberseguridad en la red de computadores
Ciberseguridad a traves de controles perimetrales y de red

# Principios de ciberseguridad en red de computadores

- Proteger
- Monitorear
- analizar 
- detectar
- responder
- proteger
- ...
Objetivo: preservar CIA y autenticación

Es necesario:
+ elementos de tecnología 
+ correcta implementación
+ personas capacitadas


Defensa de red: recaiga en equipo.

Defensa en profundidad. 
Varias capas
+ Políticas, procedimientos y concentración
	+ Política: conocidas por todos
+ Física: no se puede acceder físicamente a la red. Vigilancia
+ Perímetro: medidas de seguridad apropiadas para la protección perimetral. Acceso remoto a la red
+ Red interna. LAN
+ Servidores y equipos: cada equipo. Servidores y equipos
+ Aplicaciones: medidas de seugirdad para el aseguramiento de acceso a las apps
+ Datos: aseguramiento de datos, autenticación y autorización. Cifrado


### Aproximaciones a la defensa de red
+ aproximación preventiva: métodos que eviten ataques a red
	+ Control de acceso: firewall
	+ Control de admisión:
		+ NAC
		+ NAP
	+ Apps criptográficas
	+ Seguridad biométrica
		+ reconocimiento facial y de voz
+ Aproximación reactiva: métodos que respondan a ataques a la red
	+ Monitoreo
		+ IDS
		+ IPS
		+ SIMS
		+ SIEM
		+ TRS
	
+ Aproximación  retrospectiva: examina ataque con finalidad de encontrar la razon del mismo
	+ Diagnostico
		+ Analizador de protocolos
		+ Monitor de tráfico
	+ Seguridad forense
		+ CSIRT
		+ CERT
	+ Análisis post morten
		+ Asesor legal
		+ Asesor de riesgos
## Seguridad física
outlines the policies, procedures and technologies used to protect an area from unauthorized access, intrusion or damage

### elementos:

+ Deterrence
	+ visible security presence that makes an intruder think twice about trying to breach physical security.
+ Detection
	+ technology, personnel and resources that organizations use to detect intrusion and monitor the activity of different real-world locations and facilities
	+ EX: CCTV
+ Delay:
	+ Obstacles to make more difficult for attackers to access valuable assets and information. More time to respond and contain threats
+ Defend
	+ limiting and controlling what people can access
	+ access control: give only authorized personnel access to certain physical assets

### Why is physical security important?
data as well as where these technologies are deployed, must all be protected.

Cloud providers require: avoid data losses and uptime failures.
### Types of physical security threats

+ Human oversight. return critical equipment, such as robots or servers, to securely locked cages after a shift ends.
+ Equipment failures: can malfunction. types of surveillance mechanisms malfunction, they create vulnerabilities in physical security
+ Natural and man-made disasters


###  Developing a physical security plan

assess all corporate physical assets for level of risk and refine the scope of the plan

- Is surveillance installed at every mission-critical point throughout the enterprise and its satellite facilities?
- Are data centers and IT equipment in remote areas secured from unauthorized access?
- Are all physical security monitoring and check-in technologies such as badge scans, in-field sensors, cameras and vault locks in perfect working order?
- Are employees properly trained in physical security practices for their work areas? Are there written procedures for extenuating circumstances like storms or fires that would cause a loss of physical security?
- Are physical security guidelines and procedures documented in the corporate disaster recovery and business continuity plan, and are employees regularly refreshed on this plan and how it works? Are physical security systems regularly tested?
- Are the organization's physical assets insured for loss?

### Physical security best practices

+ **Use log and trail maintenance security.**
+ **Adopt an approach based on risk management**
+ **Tie access control to individuals**
+ **Perform regular security testing**
+ **Train employees**: physical security measures they should take in their work areas
+ **Maintain an updated plan**
+ **Determine who is in charge of physical security**
+ **Don't forget about the cloud.**: review the vendor's security audits annually
+ **Use AI with physical security.**

# Mecanismos de seguridad en el nivel perimetral y en el nivel de la red

+ Firewalls
	+ Seguridad perimetral
		+ Resistir ataques externos
		+ Identificar ataques sufridos y alertarlos
		+ aislar y segmentar distintos servicios y sistemas
		+ filtrar y bloquear el tráfico
	+ Primer defensa.
	+ Filtrado de tráfico entrante y saliente
	+ Funciones
		+ Examina tráfico
		+ Control tráfico (bloquea paquetes que coincidan con reglas de denegación)
		+ Realiza autenticación de usuarios (logs y alertar)
		+ Filtra paquetes servicios y protocolos
		+ Realiza registro del tráfico
		+ Traducción de dirección de red
		+ Filtra ataques de malware
	+ Hardware
		+ Seguridad
		+ Velocidad
		+ Interferencia mínima
		+ Costos altos
		+ Complejo implementar y configurar
		+ Más espacio y cableado
	+ Software
		+ Segunda línea de defensa
		+ Costos buenos
		+ Ideal para domésticos o pequeñas empresas
		+ Consumen recursos del sistema
		+ Dificultad de desintalar
		+ Tiempo de respuesta variable
	+ En la nube (firewall as a service)
		+ Despliegue sencillo
		+ Escalable según necesidades
		+ Protección de identidad
		+ Buen rendimiento
		+ Disponibilidad variable
		+ Pueden ralentizar red
		+ Pueden no ser eficientes al ser genéricos
+ Sistemas de detección de intrusos
	+ Busca patron de intruso diferente de usuario común
	+ Funciones
		+ Monitorear y analizar actividades de usuarios y sistema
		+ Analizar configuración de sistema y vulnerablidades
		+ Evaluar integridad de sistema y archivos
		+ Reconocer patrones típicos de ataque
		+ Analizar patrones de actividades anormales
		+ Rastrar las violaciones de las políticas
	+ Componentes
		+ Red de sesnores: log info 
		+ analizador compara contra los casos conocidos de problemas
		+ sistemas de alerta: genera la alerta
		+ Consola de comandos: interfaz entre administrador de red y sistema
		+ Sistema de respuesta: componte que genera las contra-medida cuando una intrusión es detectada.
		+ base de datos de firmas de ataques. sirve para detección de intrusión
	+ clasificación
		+ Enfoque:
			+ Basado en firmas (como un antivirus)
			+ basado en anomalías (ancho de banda, puertos, etc)
		+ Sistemas protegidos
			+ host IDS
			+ Network IDS (a todo la network)
			+ híbrido
		+ comportamiento
			+ Pasivo: monitorea, analizar y alertar
			+ activo: alerta y responde amenaza 
+ Redes privadas virtuales
	+ caracteristicas
		+ protocolos de tunelamiento o encapsulamiento
		+ Técnica de cifrado
		+ Garantiza calidad de servicio
		+ Bajo costo,
		+ Transferencia de datos seguro
		+ Permite acceso anónimo
		+ complejidad en diseño e implementación
		+ No se puede garantizar fiabilidad. Depende del proveedor
	+ dos
		+ IPsec. usa cifrado y comunicación. establecidad usando cliente VPN remoto, IntraNet y extranet
		+ SSL. navegador web y cifrado SSL. No require software adicional