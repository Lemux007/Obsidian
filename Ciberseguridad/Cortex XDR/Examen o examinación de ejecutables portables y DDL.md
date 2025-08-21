#Nodo

1. Flujo de la examinacion
	1. Un archivo que intenta ejecutarse pasa por el flujo, se llaman a varios responsables de la toma de decisiones, como origenes veredictos, listas de permitidos y listas de bloqueo:
El agente de Cortex XDR aprovecha tres fuentes de veredicto en este precedente:
- Veredictos del administrador
- Veredictos oficiales de WildFire
- Análisis Local: veredictos temporales
	![[Pasted image 20241203125158.png]]
	

  
2. Inteligencia de amenazas wildfire: Wildfire proporciona dos servicios a cortex XDR: 
		1. un servicio de analisis de archivos para crear veredictos de archivos 
		2. un servicio en la nube para proporcionar veredictos.
		 ![[Pasted image 20241203125450.png]]
		 *Static analysis*: Examina archivos sin ejecutarlos
		 *Dynamic analysis*: Ejecuta el archivo en una sandbox para observar su comportamient en tiempo real
		 *Heuristic engine*: Uso de reglas y algoritmos avanzados para identiicar patrones de comportamiento sospechoso
		 *Bare Metal analysis*: Ejecucion en HW fisico real en lugar de entornos virtuales, pues hay malware diseñado para eludir los VM.
		 Diferentes veredictos: 1. MALWARE (Archivo o url maliciosa)     2. BENIGNO (Seguro y sin amenaza)   3. GRAYWARE (Comportamiento de malware pero no malicioso)
		 
		 Hay diferencias entre BTP y Heuristic engine, BTP es en ejecucion real en el endpoint y heuristic es en un sandbox.
		 
3. Análisis local: Si el hash de un archivo ejecutable portatil o una macro no se encuentra en la cache del punto de conexion, XDR consulta el hash en wildfire. El analisis local usa un archivo modelo diferente para cada uno de los tipos de archivos: exe, dll y macro.![[Pasted image 20241203144311.png]]
4. Almacenamiento en cache de veredictos de archivos localmente: Cada agente de cortex mantiene localmente una atbla de busqueda para lmacenar los registros de examen, cadad uno de los cuales consta principalmente del hash y el veredicto de un archivo examinado y el nombre de la fuente del veredicto.

5. Poner en cuarentena automaticamente archivos maliciosos: Los archivos maliciosos cambian de formato y se envian a una ubicacion distinta. A tomar en cuenta:
	1. Restauracion manual: Se puede restaurar un archivo en cuarentena
	2. Configuracion predeterminada: La cuarentena automatica de malware esta deshabilitada por predeterminado.
	3. Limitaciones de la cuarentena: Cuarentena no aplicable a carpetas de red, volumenes de solo lectura o archivos de cifrado con EFS.
	4. Ubicaciones de archivos en cuarentena: %PROGRAMDATA%\Cyvera\QuarantineV2.

6. Como confiar en apicaciones que se publican en internet: A traves de firmas de codigo digital basado en certificados digitales.

7. Configuracion de MPM: La sección Examen de archivos DLL y ejecutables portátiles contiene varias configuraciones de MPM para el flujo de examen de archivos previo a la ejecución para decidir si se debe bloquear un archivo o permitir que se ejecute. También contiene la configuración de la ruta y la lista de permisos del firmante para eximir a un archivo del examen y, por lo tanto, permitir que se ejecute. Esta sección está disponible para que todas las plataformas compatibles examinen archivos ELF, Mach-O y APK.
   
	1. Modo de accion: deshabilitado (Detiene el flujo de examen de archivos)
	2. Poner en cuarentena ejecutables malintencionados
	3. Accion cuando el archivo es desconocido para wildfire: permite al agente XDR utilizar su motor de analisis estatico local, local analysis para determinar la probabilidad de que un archivo desconocido sea malware.
![[Pasted image 20250110160521.png]]
