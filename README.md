# Net-Sec-Solutions-SRL
NetSec Solutions SRL | Infraestructura de Red y Seguridad Integral  Este repositorio contiene la documentación técnica, scripts de automatización y archivos de configuración que componen el despliegue del proyecto final de infraestructura para NetSec Solutions SRL.   

Documentación de Infraestructura: Proyecto NetSec Solutions SRL
1. Resumen Ejecutivo
El presente proyecto detalla la implementación de una infraestructura de red corporativa robusta y segura para NetSec Solutions SRL (Empresa 1). La arquitectura interconecta tres sedes estratégicas en la República Dominicana: Santiago, Santo Domingo y La Romana, utilizando una topología Hub-and-Spoke altamente escalable mediante tecnologías de vanguardia en enrutamiento y seguridad perimetral.

2. Arquitectura de Conectividad (WAN)
La columna vertebral de la red se basa en una solución DMVPN (Dynamic Multipoint VPN) que permite la comunicación directa y segura entre sucursales:

Nodo Central (Hub): Ubicado en Santiago (R-SANTIAGO), actúa como el concentrador principal de los túneles y el punto de tránsito para el tráfico entre sedes.

Nodos Remotos (Spokes): Las sedes de Santo Domingo (SAN-DOM) y Romana (R-ROM) se conectan dinámicamente al Hub.

Cifrado de Datos: Todo el tráfico WAN está protegido mediante IPSec con algoritmos de alta seguridad (AES de 256 bits y SHA-512), garantizando la confidencialidad e integridad de la información.

Protocolo de Enrutamiento: Se utiliza OSPFv2 para el intercambio dinámico de rutas, asegurando una convergencia rápida y redundancia en el transporte de datos.

3. Segmentación y Distribución Local (LAN)
Cada sede cuenta con una segmentación basada en VLANs para organizar los departamentos y mejorar el rendimiento:

Sede Santiago (Centro de Operaciones)
Segmentos: TI (Gestión), Data Center y Administración.

Funciones: Aloja la granja de servidores que provee servicios críticos a toda la organización.

Sede Santo Domingo (Núcleo Operativo)
Infraestructura: Diseño de alta disponibilidad con switches multicapa (SWM1 y SWM2) utilizando HSRP para redundancia de puerta de enlace.

Segmentos: Marketing, RRHH, Ventas y Contabilidad.

Sede Romana (Logística)
Segmentos: Almacén, Proyectos y Gerencia.

Control: Implementación de VTP para la gestión centralizada de VLANs y seguridad de puerto.

4. Servicios de Red y Seguridad (Linux Stack)
La inteligencia de la red se apoya en dos servidores basados en Linux (10.17.0.43 y 10.17.0.44) que centralizan las operaciones:

Gestión de Identidades (AAA): Implementación de FreeRADIUS para la autenticación centralizada de los administradores en todos los equipos de red.

Servicios de Directorio y Red: Servidor dual de DHCP y DNS (via dnsmasq) que automatiza la asignación de IPs y la resolución de nombres bajo el dominio corporativo netsec.com.do.

Colaboración: Suite de mensajería corporativa configurada con Postfix (SMTP) y Dovecot (IMAP/POP3), con buzones virtuales para el personal clave.

Seguridad Interna: Uso de DHCP Snooping, Port-Security (Sticky MACs) y BPDU Guard en la capa de acceso para mitigar ataques internos y bucles de red.

Nota de Seguridad: Todos los accesos administrativos (VTY) están restringidos mediante Listas de Control de Acceso (ACL) que solo permiten la gestión desde la red de TI en Santiago, cumpliendo con los estándares de seguridad de NetSec Solutions SRL.

Componente,Detalle Técnico
Dominio Corporativo,netsec-solutions.com.do
Esquema de Direccionamiento,Privado Clase A (10.16.0.0/14 modificado)
VPN ID / NHRP,Network-ID: 10 / Auth: NetSec
Cifrado IPSec,AES + SHA-512 (Diffie-Hellman Grupo 14)
Usuario Admin,admin / N3tS3c-2025
Servidores Críticos,10.17.0.43 (RADIUS/Mail) y 10.17.0.44 (DHCP/DNS)
