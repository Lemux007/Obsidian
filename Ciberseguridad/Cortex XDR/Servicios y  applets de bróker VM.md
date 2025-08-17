# SERVICIOS Y APPLETS DE BROKER VM
1. Arquitectura de Broker VM:
   - Broker VM como plataforma: *Broker VM es un canal seguro de comunicación entre su entorno local y el servidor Cortex XDR en la nube.* Broker VM también es una plataforma para ejecutar applets, que se ejecutan como contenedores separados. Esos applets están aislados entre sí y pueden comunicarse por separado con su instancia de Cortex XDR basada en la nube.
   - Servicios de Btoker VM: On screen print, upgrade service, network service, broker vm webui service, cloud sync services, agregatos, dispatch services.
     
    Arquitectura de applets: *Los applets son servicios que se ejecutan en la maquina virtual del agente.*
    - Cada applet es un contenedor que ejecuta un servicio independiente y aislado en la maquina virtual del agente sin interferir con los demas applets que se ejecutan en la misma maquina virtual del agente.
    - Cada applet se limita a utilizar su propio conjunto de recursos
    - Los applets se activan antes de ser utilizados

	Actualmente hay seis applets iimportantes de Broker VM
	- *Local Agent Settings apple*t: El applet configuracion del agente local funciona como un *proxy* para los agentes XDR de Cortex. A pesar del nombre del applet, no hay ninguna configuracion de agente que se establezca localmente en la maquina virtual del agente. 
	  Tambien enruta las solicitudes del agente a traves de la VM del agente de vuelta a la nube y se utiliza como puerta de enlace., se conectan al puerto 8888 o al puerto especificado.
	  Cuando los agentes no se conectan a Cortex XDR, utilice este applet cuando no desee permitir el acceso directo desde sus terminales al servicio de cortex xdr
	  
	- *Syslog Collector* Applet 
	  Permite que Broker VM *reciba* los *registros* de sus *dispositivos* *syslog* de terceros o los datos de administracion de eventos e informacion de seguridad (SIEM) y los envie a cortex XDR para la deteccion de analisis y correlacion de registros
		- Servidor recopilador de syslog: Escucha en el puerto y protocolo elegido, configurados en la interfaz de cortex, Recibe los registros en ese puerto y los almacena en la memoria. El applet Syslog Collector es compatible con los formatos Common Event Format (CEF), Log Event Extended Format (LEEF), Cisco y Corelight Zeek.
		- Agregador de recopiladores de syslog: Una vez que el servidor de applets de Syslog Collector almacena los registros en la memoria, el agregador de applets de Syslog Collector lee los registros de la memoria, los agrega en lotes y comprime los lotes. Estos lotes se colocan en una cola.
		- Despachador de recopiladores de syslog: Un despachador lee un lote comprimido de la cola de lotes creada por el agregador y envía el lote a Cortex XDR a través del canal de comunicación seguro del applet con el componente correspondiente del servidor Cortex XDR.
		- Registros de applets de syslog collector: Al solucionar problemas de applet syslog collector, puede ser util examinar la configuracion del applet, el registro del applet y el registro del sensor para el applet syslog collector. El registro del sensor muestra la estadistica del applet.
	  
	- *Windows Event Collector* Applet: Se comunica con los controladores de dominio de windows
		- Applet y controladores de dominio de WEC
		- Eventos y registros
		- Funcionamiento del applet WEC
		- Configuracion del applet WEC
		- Activacion del applet WEC
		- Probando el applet del WEC
		- Condiciones para darse de baja 
		- Registros para el applet del WEC
	  
	- *Network Mapper* Applet: Busca *dispositivos no administrados* en una red interna
		- Gestion de activos de Cortex XDR: La visibilidad de activos de red ayuda a detectar dispositivos no autorizados en una red y a prevenir actividades maliciosas.
		- Mapeador de red: Realiza exploraciones de red para encontrar e identificar dispositivos no gestionados conectados a la misma red
		- Escaneo con Nap: Usa nmap para su escaneo, inicia exploraciones syn del protocolo de mensajes de control de internet (ICMP) o del protocolo de transmision (TCP) en los puertos o rangos de puertos elegidos.
		- Requisitos del mapeador de red: asegurarse que la maquina virtual tenga acceso a toda la red interna, especificar numero de solicitudes, de nmap por segundo.
		- Registros para el applet del mapeador de red: Al solucionar problemas del mapeador de red, puede ser util examinar la config del applet, el registro del applet y el registro del sensor para el applet.
	  
	- *Pathfinder* Applet: *Proporciona analisis en busca de host no administrados sospechosos*. Pathfinder recibe una solicitud de XDR para realizar un analisis y utiliza las credenciales proporcionadas previamente para ejecutar el analisis.
		- Cuando pathfinder ayuda: Cuando Cortex XDR recibe registros EDR de un agente de Cortex XDR, reconoce ese punto final como administrado. Pero cuando Cortex XDR recibe registros de terceros y registros de red de Next-Generation Firewall (NGFW), y los análisis que incorporan esos registros muestran actividad sospechosa, Pathfinder envía una carga útil que recopilará información del endpoint para verificar la actividad sospechosa.
		- Comunicacion pathfinder: Pathfinder utiliza el protocolo Server Message Block (SMB) para comunicarse y transferir la carga útil al punto final para realizar su escaneo. Los resultados del análisis se devuelven al servidor Cortex XDR con más información sobre un punto de conexión no administrado.
		- Autenticacion de pathfinder: Pathfinder se configura en el momento de la activación. Los clientes eligen entre Kerberos y la autenticación de administrador de LAN (NTLM) de nueva tecnología. Cuando se configura Kerberos, Pathfinder intentará obtener el nombre de dominio completo (FQDN) del host para que pueda obtener un vale de autenticación del servidor de autenticación; su servidor DNS debe admitir esta búsqueda inversa.
		- Operacion de pathfinder: Enviara un script powershell firmado y una carga util al punto de conexion e informara sobre el exito de la instalacion de la carga para la auditoria.
		- Carga util de pathfinder: Despues de comprobaciones el script ejecuta la carga util. La carga util es un recopilador de datos EDR que recopila informacion y la envia al servidor Cortex XDR.
		- Registros para applet pathfinder: Util mirar el registro del applet de pathfinder y el registro de actividad
	  
	- *CSV collector* Applet: Permite *supervisar* y *recopilar* archivos de *registro* *CSV* de un directorio compartido de windows directamente en el repositorio de registros con fines de consulta y visualizacion.


[[Características Adicionales del producto bróker VM]]
[[Bróker VM setup]]