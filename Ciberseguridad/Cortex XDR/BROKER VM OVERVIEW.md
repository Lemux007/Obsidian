# INTRODUCCION A BROKER VM
1. Broker VM como canal de comunicaciones: Algunos puntos de conexión de la red interna utilizan agentes de Cortex XDR para comunicarse con Cortex XDR. Incluso cuando los dispositivos no ejecutan agentes, Broker VM proporciona un canal de comunicación alternativo y seguro para comunicar información relacionada con la seguridad a los servidores Cortex XDR.
   - Agentes: Cortex XDR se compone del trabajo combinado de Cortex XDR, que reside en Google Cloud Platform (GCP), y agentes y dispositivos de terceros que forman parte de su centro de datos, infraestructura híbrida o en la nube.
   - Sin agentes: Los sensores de terceros, como los servidores syslog y los firewalls que no son de Palo Alto Networks, necesitan un agente que reenvíe su información a Cortex XDR, y los usuarios necesitan un canal seguro a la nube para esta información en la que Cortex XDR confíe.

2. Maquina virtual de agente en Cortex XDR: Este diagrama muestra la funcion de Broker VM que conecta XDR y las redes internas con los usuarios.
   Se comunica entre sus redes y la funcionalidad de cortex XDR proporcionada en la nube.
   - Comunicacion segura
   - Redireccion de datos
   - Objetivos de datos
![[Pasted image 20241212102522.png]]
	Red interna del cliente: Puede contener puntos de conexion, servidores, dispositivos de terceros o centros de datos. agentes de Cortex XDR, firewalls de PAN, firewalls de terceros y otras fuentes de alertas y registros enrutan los datos a traves de Broker VM a Cortex XDR.

3. Broker VM como plataforma: Cortex XDR proporciona una funcionalidad que necesita información de sus dispositivos locales y sensores de seguridad. Por ejemplo, Cortex XDR proporciona a los analistas de seguridad una herramienta de análisis de causa raíz para identificar la causa raíz de un incidente. Esta herramienta, al igual que muchas otras, requiere información de dispositivos y sensores de seguridad (endpoints).
   - Reemplazo de varios agentes: En lugar de requerir que cada aplicación tenga su propio agente en los puntos finales de los usuarios, Broker VM es un agente unificado que recopila toda la información y la pone a disposición de Cortex XDR. Hay una máquina virtual de Broker instalada en las instalaciones del usuario, y cada servicio de Cortex XDR que necesita algo del entorno local tiene un applet de máquina virtual de agente que lleva la información a la máquina virtual de Broker, que a su vez informa de esta información a las aplicaciones basadas en la nube.
   - Prestacion de servicios de Cortex XDR: Los applets proporcionan servicios de Cortex XDR a los usuarios, y la máquina virtual de Broker ejecuta diferentes applets por separado en la máquina virtual mediante la autenticación del servidor de Cortex XDR. Diferentes applets sirven para diferentes propósitos. Actualmente, Broker VM admite los applets Configuración de agente local, Syslog Collector, Windows Event Collector, Network Mapper y Pathfinder.

--- 
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
---
# CARACTERISTICAS ADICIONALES DEL PRODUCTO BROKER VM
1. Caracteristicas de la maquina virtual del agente
	1. Actualizaciones y mejoras de Broker VM: Una vez instalado, el broker recibe automáticamente actualizaciones y mejoras de Cortex XDR, y esta disposición proporciona a los usuarios nuevas capacidades sin necesidad de instalar una nueva máquina virtual. 
	   Cada vez que el servidor Cortex XDR detecte que hay un nuevo paquete de actualización disponible para la máquina virtual del agente, enviará una notificación a la máquina virtual del agente de que hay un paquete de actualización disponible.
	   
	   1. Linea de comandos: La maquina virtual de broker tiene su propia interfaz de usuario web independiente de la consola de administracion de cortex XDR, los administradores pueden acceder a la linea de coandos de Broker VM mediante SSH dentro de la consola de Broker VM o a traves de Remote Terminal desde la consola de Cortex XDR.
	   2. Interfaz de escucha proxy: Puede configurarse, esto se hace durante la activacion del applet configuracion del agente local en la maquina virtual del agente.
	   3. Registros de PingFederate: Puede ingerir registros de pingfederate.

___
---
# BROKER VM SETUP
___
---

# INSTALAR EL AGENTE CORTEX XDR
1. Acceso a cortex XDR: Acceda a cortex XDR desde un navegador en el endpoint en el que desea crear un paquete de instalacion y descarge el paquete de instalacion.
   - URL for cortex XDR agent
   - Log in to Cortex XDR
   - Wait for interface to load
   - View cortex XDR dashboard

2. Pagina de instalacion del agente: Genere un paquete de instalacion del agente ("Instalador") desde la pagina de instalaciones del agente de la consola de administracion de Cortex XDR y descarge el archivo
	1. Menu desplegable de puntos de conexion: **Endpoints > Endpoints managment > Instalaciones de agente**
	2. Crear un nuevo instalador: boton crear
	3. Progreso de la instalacion del agente: Completar camposs y damos en crear nuevo instalador y crear.
	4. Instalacion del agente completada: Con estado completado
	5. Menu desplegable: Una vez creado de click derecho y escogemso 32 o 64 bits
	6. Buscar y ejecutar el paquete de instalacion: 
	7. Permita el control de cuentas de usuario: dar en si
	8. Dar finish
	9. Agente habilitado

# DESCARGAR UN ARCHIVO OVA PARA BROKER VM
1. Imagenes de Broker VM: Obtenga imágenes de máquina virtual de Broker a través de la consola de administración de Cortex XDR, a la que accede iniciando sesión en el inquilino de Cortex XDR. La imagen de máquina virtual de Broker que utilice depende del entorno de máquina virtual. Palo Alto Networks proporciona tipos de imágenes de VM de Broker para varios entornos de hipervisor estándar.
   - Disco duro virtual (VHD)
   - Disco de maquina virtual (VMDK)
   - Dispositivo virtualizado abierto (OVA)

2. Descargar archivo OVA para ESXi: Se accede a las imagenes de VM a traves de la consola de administracion de cortex XDR. Pasos:
	1. Acceda a la consola de administracion Cortex XDR
	2. Seleccionar configuraciones
	3. Seleccione Broker VM

3. Descargar archivo OVA: Puede seleccionar el formato de archivo OVA desde la consola de administracion de Cortex XDR y descargarlo en su equipo local.

# INSTALACION DE LA MAQUINA VIRTUAL DEL AGENTE
1. Conexion de la maquina virtual del agente a la instancia de XDR: Se utiliza un token para conectar la maquina virtual de Broker a la instancia de Cortex XDR
   Como generar y utilizar un token:
   1. Generar token: En la pagina de broker VM de la consola de cortex clic en generate token
   2. Copiar token
   3. Crear una contraseña unica: Cargue la imagen OVA en su entorno ESXi y acceda a ella mediante su direccion ip asignada como un navegador.
   4. Registro del Broker VM local: Una vez aplicada la contraseña damos clic en regitrarse
   5. Pega tu token guardado

# CONFIGURACION DE LA MAQUINA VIRTUAL DEL AGENTE
1. Acceso a la maquina virtual del broker para la configuracion: La maquina virtual del agente registrada se configura desde la pagina Maquinas virtuales de agente de Cortex XDR
   - Acceso a cortex XDR: Despues de registrar la VM una ventana indicara que inicie sesion en la consola de administracion de cortex
   - Ver maquina virtual de agente en la pagina maquinas virtuales de agente: En el menu desplegable de engranaje de configuracion seleccione configuraciones y vaya a broker VM en el panel de navegacion izquierdo.

2. Cambiar los parametros de configuracion de la maquina virtual del agente: La mayor parte de lo que se puede ver en la fila de la maquina virtual del agente de la pagina Maquinas virtuales del agente se puede configurar mediante menus desplegables de la lista de maquinas virtuales de agente.
   - Menu de VM de Broker: Proporcina acceso a la gestion de broker y sus applets
   - Menu contextual de administracion de corredores: Administracion del agente en el menu contextual
   - Opcion del menu configurar: Al elegir la opcion configurar en el submenu administracion de agentes para configurar la maquina virtual del agente, se accede en la pagina configuraciones de maquinas virtuales del agente.

# ACTIVAR APPLETS DE MAQUINA VIRTUAL DE BROKER
1. Menu de VM de broker y activacion de applet: En el menú Máquina virtual de agente de cada máquina virtual de agente se enumeran los applets disponibles. Para cada applet inactivado, el único submenú es su activación. Por ejemplo, la selección del recopilador CSV del menú VM del agente tiene un submenú con Activar como opción. Al seleccionar **Activar** para el **recopilador de CSV**, se accede a la página Activar applet del recopilador de CSV.
2. Activacion del applet del recopilador de syslog: Como ejemplo de lo sencillo que puede ser activar un applet, en esta seccion se muestra la activacion del applet syslog collector:
	1. Eleccion del menu activar el recopilador de syslog: Inicie la activación de **Syslog Collector seleccionando Syslog Collector** y **Activate (Activar**) en el **menú Broker VM (Máquina virtual del agente**).
	2. Pagina del recopilador de syslog: La selección del menú Activar le lleva a la página del recopilador de Syslog. El applet Syslog Collector está configurado de forma predeterminada para detectar automáticamente todos los formatos, proveedores y productos, y aceptar datos de cualquier red.
	3. Boton de activacion del recopilador de syslog: Se activa simplemente haciendo clic en el boton activar en la pagina del syslog collector. 

---
---
# BROKER VM MANAGEMENT
---
---
# DETALLES DE CONFIGURACION DE BROKER VM
1. Configuraciones de Access Broker VM: ***Clic detecho en la VM > Administracion de agente > Configurar***
   - Maquinas virtuales de broker registrado: Muestra las maquinas virtuales de broker registradas en este inquilino de cortex xdr
   - Encabezados de columna: Muestran oara cada broker VM el nombre del dispositivo, la interfaz externa, todas las interfaces, la version del broker VM, estado de configuracion, uso de CPU, uso de memoria, uso del disco.
   - Columna aplicaciones: Estado de activacion de los applets de broker vm

2. Ver y editar detalles de configuracion: Los detalles de configuración se agrupan en categorías en la página Configuraciones de máquina virtual de agente. En esta sección se muestra cómo ver y editar las configuraciones asociadas a cada grupo. Los detalles de configuración se pueden ver incluso cuando la máquina virtual de Broker no está conectada a Cortex XDR. Sin embargo, estos detalles solo se pueden editar cuando la máquina virtual de Broker está conectada a Cortex XDR. Se accede a los grupos de configuración mediante selección desde el panel de navegación izquierdo de la página Configuraciones de VM de agente.
   - Nombre del dispositivo y su FQDN
   - Interfaces de red: En el panel de navegacion izquierdo, los detalles de config de la interfaz de red incluyen el nombre y la ip, MAC y si la direccion es estatica o dinamica.
   - Servidor proxy: Broker vm se puede configurar para usar un servidor proxy para comunicarse con cortex XDR o acceder a internet. Para configurar un proxy de maquina virtual de agente, seleccione **Servidor proxy** en el panel de navegacion izquierdo. Protocolos: Socks4 o socks5
   - Protocolo de tiempo de red (NTP): La configuracion de NTP es esencial para el registro correcto y para la sincronizacion del reloj entre el recopilador de syslog y otras aplicaciones y servicios.
   - Actualizacion automatica: Nuevas funciones y mejoras
   - Acceso SSH: Las conexiones ssh a la maquina virtual del agente se pueden habilitar o deshabilitar, el acceso ssh se autentica mediante una clave publica, concede acceso remoto a la instancia de vm de broker

# REGISTROS DE BROKER VM
1. Descargar registros: Se almacenan en broker VM y se pueden ver alli o descargarse desde la pagina Broker VMs de la consola de administracion de Cortex XDR. Seleccione **Administracion de agentes > Descargar los registros mas recientes**

2. Ver registros: Los registros ayudan a supervisar el uso de la administracion, el rendimiento, las redes, los applets y los servicios internos de broker VM. Tambien pueden ayudar con la solucion de problemas.
   Carpeta de estadisticas: Se puede ver que hay archivos de texto con estadisticas recopiladas de una variedad de recursos del sistema y de la red.

3. Carpeta de autenticacion: Tiene un archivo de registro. En este archivo registra las actividades de autenticacion como la creacion de usuarios y el inicio y cierre de sesion.
   - Abra la carpeta de autenticacion
   - Abrir el archivo auth.log con cualquier editor de texto o visor, como el bloc de notas
   - El archivo auth.log muestra la secuencia de actividades de autenticacion, como la creacion de usuarios y grupos, el inicio y cierre de sesion y otras actividades relacionadas.

4. Carpeta de registros: contiene los registros de los applets de broker VM
   - Carpeta de registros: Contiene registros de los applets de broker vm como los registros del applet syslog collector en la carpeta anubis, registros de applet network en network_mapper y applet pathfinder en odysseus
   - Registros de servicios internos de broker VM: Los registros de sincronizacion en la nube estan en cloud_sync.log y los registros de instalacion estan en clean_installation.log servicio de mensajeria en rabbitmq_watchdog.log
   - Registro de la consola: Podemos ver actividad como la rehabilitacion y deshabilitacion de la interfaz de usuario web de broker vm

# REINICIAR BROKER VM
1. Pasos: Seleccione reiniciar maquina virtual: En el submenu administracion de agentes del menu de la maquina virtual de agente, seleccione **Reiniciar maquina virtual**
2. Haz clic en reiniciar
3. Comprobar la confirmacion
4. Maquina virtual del agente de acceso: Cuando intenta acceder a la instancia de broker vm directamente desde un explorador mediante su direccion ip o FQDN, no puede porque la instancia de maquina virtual de broker esta en proceso de reinicio.

# LIVE TERMINAL BROKER VM
1. Conexion de terminal en vivo broker vm: Puede acceder a la linea de comandos del broker directamente desde la consola de gestion de Cortex XDR. puede utilizar la linea de comandos de broker VM para hacer cosas como acceder a los registros broker VM; realizar manipulaciones de archivos, reiniciar, detener y comprobar el estado de los applets; iniciar, detener y comprobar el estado de los servicios internos del broker VM; restablecer la contraseña de la interfaz de usuario web de la maquina virtual del agente; y usar comandos estandar de linux, como comandos, para capturar el trafico de red.