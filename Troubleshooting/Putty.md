#Nodo
Configuraciones [[PAN]] en Putty
# Factory reset
Entrar al CLI por serial y administrador de servidores
- debug system maintenance-mode
Vamos al menú y damos en factory reset
Dejamos activadas las opciones del panos en using image y nnsa
Y hasta que cargue y lo reiniciamos

Iniciamos en sysroot0


# Configuración de inicio 
Desactivar ZTP: set system ztp disable

- configure
- set deviceconfig system ip-address 192.168.78.252
Si la queremos colocar por DHCP le damos: 
- configure
- set deviceconfig system type dhcp-client
- set deviceconfig system dhcp-client-options accept-dhcp-domain no
- set deviceconfig system dhcp-client-options accept-dhcp-hostname no
- set deviceconfig system dhcp-client-options send-client-id no
- set deviceconfig system dhcp-client-options send-hostname no
- commit

Configurar los servicios DNS en DEVICE/Setup/services y colocamos el primario y secundario

Firewall de inspección de paquetes de estado: Basados en puertos y dependen en gran medida de la confiabilidad de los dos host, ya que los paquetes no se inspeccionan despues de establecer la conexion.
Operan hasta la capa 4 (transporte) y mantienen información de estado sobre las sesiones de comunicación que se han establecido entre hosts en dos redes diferentes.

Firewall de aplicaciones: Los Firewalls de aplicaciones a tercera generación tambien se conocen como puertas de enlace de capa de aplicación FW basados en proxy y firewalls de proxy inverso.

# Reiniciar management
- debug software restart process management-server

# Instalar dynamic updates
Recuperar todos las licencias en device > licenses
check now en los dynamic updates o software si por ahí no nos salen.
Descargar e instalar todas las updates 
![[Pasted image 20250730113304.png]]