## Componentes

+ Transmisión cifrada, 
+ IPsec, 
+ Firewall, 
+ Zona desmilitarizada ​DMZ, 
+ Zona de guerra, 
+ Redes privadas virtuales, VPN. 
+ Conexiones WAN, 
+ Red de los operadores de telecomunicaciones, ​
+ Zona inalámbrica, 
+ Entre muchos otros. ​

## como los integramos?

En la arquitectura y su integración. Generamos anillos 
### Anillos

*anillo perimetral*: a traves de firewall, IPS, UPS

*Anillo de red corporativa*: equipos de comunicaciones: conmutadores, switch, enrutadores 

*anillo de sistema operativo*: firewall, control de aplicaciones, antimalware, etc
*Anillo de Nivel aplicaciones / base de datos*: 

si lo cumplimos todos, tenemos una infraestructura de ciberseguridad. 

> Ninguna aplicación es 100% segura

#### Zona de servicios LAN

+ Serivcios misionales corporativos:
+ Criticos: 
	+ aplicaciones, 
	+ correo electronicos 
	+ Base de datos
	+ Aunque peude estar en otro lado
+ Protegiso opr UTM (firewall). Otro servicio (fuera de LAN) requiere algo, entonces pasa por firewall, se valida y se redirige a la 
+ DMZ: recibe conexiones- Intermediaro

Pasos
+ Solicitud de Internet o WAN 
+ Firewall aplica reglas configuradas
	+ Puede temrinarlas o redigirlos a DMZ
+ DMZ: pide ingreso al firewall a la red LAN
+ LAN: recibe conexión y responde a DMZ.
+ DMZ responde, pasando por firewall al servicio original

#### WAN: 
nos conectamos a sedes corporativas remotas. Depende de configuraciones.

Se recomienda conexiones a traves del firewall

#### Zona inalambrica
Adminsitrada de diferenetas maneras
+ Mecanimso de seguridad a traves de access point. ACL
+ Conexiones aseguradas a traves de WPA3 (por ejemplo)
+ WLC (controladores inalambrica LAN)
	+ Definir: cifrado, VPN, manejo de integridad, autenticación, etc

#### Zona administración
+ Administración infra y servicios TI
+ Perfiles de usuairo con privilegio de admin
+ A traves de LAN y firewall perimetral, adminsitrar tipo de conexiones permitidas.
+ Gestor de logs (con redundancia).
IPsec. VPN general


#### Zona de usuarios
Se encuentran todos los usuarios que se encuentra en la organización. VLANs, redes virtuales. Y teniendo firewall perimetral. 
Ubicar otras controles: arpWatch (cambios de IP y MAC (ARP spoofing))

### IDS
Herramientra analiza trafico de red, NIDs o comportamiento anómalos del sistema (HIDS.

Si detectan tráfico o comportamineto anómalo, generan alerta. 
Se pueden configurar como IPS (sistema de prevención de intrusos, bloquea el tráfico)

Se encuentra dentro de las zonas, además de la UTM.

# Configuración de IPSec

Objetivo

Manejar: confiencialidad, autenticación, integridad entre par de equipos.

## Video

Usar 2 VMs
Hacne ping entre las dos

Despues pone wireshark, vé que se manda en texto plano.

Muestra IPSec, para hacer tunel entre las 2 VMs.

Muestra que una vez que se hace el tunel, no se muestran ICMP, así como tampoco HTTP

# Que es la ciberseguridad?

Práctica de defender las computadoras, los servidores, los dispositivos móviles, los sistemas electrónicos, las redes y los datos de ataques maliciosos

Categorias:
+ **seguridad de red** es la práctica de proteger una red informática de los intrusos
+ **seguridad de las aplicaciones** se enfoca en mantener el software y los dispositivos libres de amenazas. 
+ **seguridad de la información** protege la integridad y la privacidad de los datos
+ **seguridad operativa** incluye los procesos y decisiones para manejar y proteger los recursos de datos
+ **recuperación ante desastres y la continuidad del negocio** definen la forma en que una organización responde a un incidente de ciberseguridad o a cualquier otro evento que cause que se detengan sus operaciones o se pierdan datos
+ **capacitación del usuario final** aborda el factor de ciberseguridad más impredecible: las personas. Mantener buenas prácticas de seguridad.

## Extensión de ciberamenzanas

Mucho, cuestan 260.000 millones de dolares en 2026.

## Tipos

+ *Delitos cibernético*: agentes individuales o grupos. Atacan sistemas por plata o interrupciones
+ *Ciberataques*: recopilación de info con fines políticos
+ *Ciberterrorismo*: objetivo debilitar los sistemas electrónicos para causar pánico o temor.

Métodos más comunes para amenzar la ciberseguridad:
+ *Malware*: software malicioso. Software creado para interrumpir o dañar equipo de usuario legítimo.
	+ *Virus*: programa capaz de reproducirse, que se incrusta un archivo limpio y se extiende por todo el sistema informático e infecta a los archivos con código malicioso
	+ *Troyanos*: se disfraza como software legítimo. Los cibercriminales engañan a los usuarios para que carguen troyanos a sus computadoras, donde causan daños o recopilan datos.
	+ *Spyware*: registra en secreto lo que hace un usuario para que los cibercriminales puedan hacer uso de esta información
	+ *Ransomware*: bloquea los archivos y datos de un usuario, con la amenaza de borrarlos, a menos que se pague un rescate.
	+ *Adware*: software de publicidad que puede utilizarse para difundir malware.
	+ *Botnets*: computadoras con infección de malware que los cibercriminales utilizan para realizar tareas en línea sin el permiso del usuario
+ *Inyección código SQL*: tomar el control y robar datos. Instrucción SQL maliciosa.
+ *Phishing*: correos electrónicos que parecen de empresa legítima solicitando info confiencial
+ *Man-in-the-middle*: intercepta la comunicación entre dos individuos para robar datos
+ *Ataque de denegación de servicio*: impiden que un sistema informático satisfaga solicitudes legítimas sobrecargando redes y servidores con tráfico.

## Protección del usuario final

Ciberseguridad depende de protocolos criptográfico para cifrar correos electrónicos, archivos y datos críticos. Protege: info en tránsito, además de pérdidas y del robo.

+ software de seguridad del usuario final: 
	+ analiza computadores para detectar código malicioso, ponerlo en cuarentena y eliminarlo. 
	+ Detección de malware en tiempo real. Análisis heurístico y comportamiento para monitorearlos.
	+ Algunos usan burbujas virtuales para analizar su comportamiento y aprender a detectar mejor nuevas infecciones.
## Consejos de ciberseguridad: protéjase de los ciberataques

+ Actualizar software y sistemas operativos: para usar últimas revisiones de seguridad
+ Usar antivirus: para detectar y elimianr amenazas
+ Utilizar contraseñas segurdad
+ No abrir archivos adjunto de correos electrónicos de remitetnes desconocidos.
+ No haacer clic en correo electrónicos de remitentes o sitios web desconocidos
+ Evitar uso de redes WiFi no seguras en lugares públicos

# Arquitectura de Seguridad Informática



## Que es?

Es el entendimiento de riegos para la seguridad de la información y los procedimientos para su implementación.

Que controles implementamos para mantener la ciberseguridad

Ataques

### CIA
+ confidencialidad: solo los usuarios correctos debe poder  él acceder a los datos, . 
+ integridad: no se deben poder modificar sin permisos. 
+ disponibilidad de datos

Hackers contrario:
+ Extracción
+ Modificación
+ Negación de datos

Arquitectura más conocida:
ISO 27001: objetivo ir hasta ahí

Controles:
+ Objetivo: bloquear los 3 selectores de ataque más comunes
+ Exploits
+ Password default
+ Brutefored
+ Interrupción de sesion
+ Phising
+ Sitios infectado
+ Virus
+ Gusandos
+ Troyanos
+ Ingenieria social
+ Ataque inalambrico
+ Robo fisico del equipo
+ Acceso físico

Solo 6 cosas:
+ Prevenir intrusión
+ detectar intrusión
+ Prevención de extacción
+ Prevención de modificación
+ Eliminación de intrusión
+ Prevención de negación de servicios

27 controles:
+ Firewall, ruteadores y switches
+ Implementación segura de DNS
+ Admin de password
+ Inventario de hardware, software, puerots y servicios y GUIs
+ Escaneo y remediación de vulnerabilidad
+ Endurecimiento de servidores y PCs
+ Protección de base de datos
+ Antimalware
+ Protección de platamoras moviles
+ Filtrado de email y sitios web
+ Sistemas de prevención y detección de intrusión (IPS)
+ Análisis de bitácoras (logs)
+ Análisis de tráfico
+ Monitoreo de integridad de archivos
+ Prevención de pérdida de datos
+ Encripción de datos en transmición y almacenamiento
 + Defensa en contra de denegación de servicios
 + Entrenamiento a usuarios
 + Control de acceso físico
 + Pruebas de penetración: forma activa de buscar vulnerabilidades
 + Plan de respuesta a incidentes

### UTM: (administración unificada de amenazas) 
Múltiples funciones o servicios de seguridad se combinan en un solo dispositivo dentro de su red

Características deseasdas:
+ Antivirus
+  Antimalware 
+ Firewall
+  Prevención de intrusiones 
+ VPN
+ Filtrado web (no vayan a ciertos sitios web)
+ Prevención de pérdida de datos

Ventajas

+ Flexiblidad y adaptabilidad
+  Integración y gestión centralizadas 
+ Rentabilidad
+  Mayor conciencia de las amenazas de seguridad de red 
+  Solución de seguridad más rápida para empresas 
+ Cortafuegos de próxima generación frente a UTM