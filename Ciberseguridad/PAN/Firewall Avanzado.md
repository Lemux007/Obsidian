#Nodo

TEMARIO EXAMEN FIREWALL AVANZADO 
 Servicios IP DHCP Server, DHCP Relay, DNS Proxy 
 Enrutamiento Dinámico OSPF 
 Global Protect Creación del Portal y Gateway. Aplicaciones clientless 
 QoS Políticas y monitoreo
 Perfiles de Seguridad URL, Threat Prevention, Antimalware y antispyware.


![[Pasted image 20260327113444.png]]

IP interface LAN 192.168.78.254/24

Zona Untrust interface 1/1 192.168.78.252/24
Zona Trust Interface 1/2 10.1.1.1/24
Zona DMZ interface 1/3 172.16.1.254/24
Interface de administracion 192.168.78.252

1. Comprueba que el equipo conectado a las zonas Trust y DMZ puedan tener acceso a Internet. (Se evalúa, ruteo, reglas de NAT y Seguridad)

2. Configura el servicio de relay de DHCP. El servidor de DHCP de la red es el host 192.168.78.254.
3. Configura OSPF con el área 0.0.0.3 y los siguientes parámetros:

	- Hello Interval:10
	- Dead Counts:4
	- Retransmit Intervals: 5
	- Graceful Restart Hello Delay: 10
	- Metric: 10
	- Priority
	- Auth Profile: None
4. Configura la VPN de Global Protect y compruebe que el portal sea visible.
5. Configura un NAT-U Para poder visualizar el portal de Global Protect desde la red Interna
6. Configura el QoS a manera que se pueda visualizar el gráfico de consumo en tiempo real de interface de red perteneciente a la LAN
7. Configura el DNS Proxy para que el PAN pueda operar como servidor DNS. Tomar los DNS 8.8.8.8 y 4.2.2.2
8. Configura un perfil de Threat Prevention en el cual las amenazas de nivel crítico, alta y medio tengan como acción la de Default y para las amenazas de nivel bajo e informacional la acción sea Alert.
9. Del perfil de seguridad anterior, crea una excepción de la vulnerabilidad ID 32422 para que permita el tráfico pero que se registre el evento.
10. Configuración de una aplicación Clientless en portal de Global Protect. La aplicación puede ser la misma consola de administración del equipo PAN