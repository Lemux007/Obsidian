#Nodo
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


[[Habilitación del servicio de CORTEX XDR EDL]]


