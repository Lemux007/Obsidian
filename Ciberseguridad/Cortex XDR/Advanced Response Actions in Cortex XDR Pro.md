SUGERENCIAS DE CORRECCION
1. Acciones de respuesta avanzadas: Algunas acciones de respuesta de XDR requieren: 
   - licencias
   - autorizacion
   - configuraciones adicionales,
   - Compatibilidad con el sistema
   Estas acciones incluyen: Sugerencias de corrección, ejecuciones remotas de scripts y EDL.
2. Acciones de sugerencia de corrección
   XDR Permite la reversion de los cambios realizados por procesos maliciosos. Ej:
   - Revertir archivos y claves del registro modificados con fines malintencionados
   - Las sugerencias de correccion estan disponibles para Windows con la licencia de XDR Pro terminal
   - La recopilacion de datos de endpoint mejorada debe estar habilitada
		- Menu contextual de un modo de proceso
		- Menu acciones de la vista de causalidad
		- Menu de tres puntos de un incidente

3. Lista de sugerencias de corrección
	Al iniciar las sugerencias de corrección, aparece un cuadro de dialogo que muestra una tabla con entradas que muestran eventos de proceso malintencionados.
	- Columna de correccion sugerida: Muestra una accion de correccion recomendada para revertir eventos de procesos malintencionados
	- Seguimiento del estado de correccion: O del estado de la accion desde el centro de actividades
	- Realizar acciones de forma masiva: Seleccionar varias entradas de evento > menu contextual > remediar
	- Revisar los detalles del incidente: Completado en el titulo muestra el fin.

4. Soluciones sugeridas: La columna correccion sugerida muestra las posibles acciones de correccion, incluida la correcion manual para los casos en que XDR no pueda proporcionar una accion de correcion.
   Sugerencias de mediacion:
   - Eliminar, restaurar o cambiar el nombre del archivo
   - Eliminar o restaurar el valor del registro
   - Terminar la causalidad
   - Correccion manual


EJECUCIONES REMOTAS DE SCRIPTS
1. Bibliotecas de scripts: Puede cargar y ejecutar de forma remota scripts de python v3.7 desde el centro de actividades > la biblioteca de scripts del agente
	- Cargue Scripts de python listos para usar: La biblioteca muestra scripts de python listos para usar escritos por PAN
	- Agregar un nuevo script: Abrir el menu contextual de un script para ejecutarlo, editarlo o eliminar.

2. Mapeo de entrada/salida ilustrado
   ![[Pasted image 20241205172001.png]]
3. Scripts en ejecucion, Pasos:
   - Click derecho y run
   - En elegir introducimos la entrada del script tal y como se definio durante la carga, IP (STRING), el punto de entrada del script y 192.168.1.2 el valor del parametro ip
   - Destino, seleccionar uno o varios puntos de conexion para ejecutar el script
   - Realice un seguimiento de la accion de ejecucion de scripts de punto de conexixon desde todas las acciones del centro de actividades
   - El cuadro de dialogo de datos adicionales muestra los parametros generales de ejecucion del script en la parte superior y la tabla de resultados de ejecucion en la parte inferior.
	   - Nombre del script
	   - Entry point como el nombre de la funcion llamada
	 
	 Ejecución de scripts desde todos los puntos de conexión, es un metodo alternativo para ejecutar scripts de endpoints **Endpoint Control > Abrir un modo interactivo** directamente en la consola de administracion.

	Ventajas de ejecutar scripts en modo interactivo:
		1. Ejecute varios scripts en el mismo conjunto de endpoints seleccionados
		2. Realice un seguimiento del progreso de las ejecuciones de scripts en tiempo real desde el cuadro de dialogo interactivo
		3. Vea los valores devueltos en tiempo real


HABILITACION DEL SERVICIO DE CORTEX XDR EDL
1. Listas dinamicas externas (EDL): Tipo de lista de bloqueo en la que cada linea es una direccion IP separada o una entrada de nombre de host que se va a bloquear.
   - Consumidores tipicos de EDL son NGFW (PAN-OS)

2. Tareas de servicio EDL: EDL tiene una configuracion global **Configuracion > Integracion**, como una tarea de una sola vez, la configuracion incluye la habilitacion global del servicio EDL de cortex XDR.
   sd
   - Despues de establecer el parametro EDL hay dos tareas de administrador diferentes en curso: Agregar direcciones IP y dominios a las listas EDL y administrar las listas EDL
   - Puede agregar direcciones IP y dominios maliciosos a las listas de EDL desde varias paginas de la consola de administracion, incluido el centro de actividades menu de respuesta > EDL
   - Puede administrar las listas d eEDL desde el **Centro de actividades > acciones aplicadas actualmente > Lista dinamica externa**
	
	Configuracion global de EDL
	- Config de autenticacion para conectarse al servicio EDL
	- Boton de activacion/desactivacion para el servicio EDL
	- Las URL de las dos listas EDL: Direcciones IP EDL y nombres de dominio EDL
	- Formato de URL. https://edl-|subdominio|.xdr|region|.paloaltonetworks.com/block_list?type=ip

3. Adicion de direcciones IP Y HOST A EDL
   Puede agregar direcciones IP y dominios maliciosos a las listas de EDL desde varias paginas de la consola de administracion. 
   **Respuesta > EDL**
   **Centro de actividades > Agregar EDL**
   **Quick Launcher**
   **vista de IP**

4. Gestion de EDL en el centro de accion
   A medida que se agrega ip y dominios a las EDL cortex mantiene sus adiciones en dos listas accesibles desde **Centro de actividades > Acciones aplicadas actualmente > Lista dinamica externa**


