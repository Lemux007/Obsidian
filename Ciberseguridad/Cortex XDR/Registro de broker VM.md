#Nodo
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
