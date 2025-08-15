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
[[Servicios y  applets de bróker VM]]
[[Bróker VM setup]]


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