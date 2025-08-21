#Nodo

1. Pagina del centro de consultas: Puede administrar consultas en la pagina centro de consultas de la consola de administración.
   - **Tabla de consultas ejecutadas**: La pagina centro de centro de consultas de la consola de administración muestra una tabla de consultas ejecutadas.: Mostrar resultados, Copia URL de consulta, cambiar nombre, volver a ejecutar consulta, guardar como una nueva consulta, programar y quitar.
   - **Acción de consulta ejecutadas**: Hay varias acciones en el menú contextual que se pueden realizar en las consultas ejecutadas
	   - Volver a ejecutar la consulta, al volver a ejecutar una consulta, XDR crea una nueva consulta con el mismo nombre de consulta que que la de origen. el ID se crea de nuevo. 
	   - Consulta programada: Puede programar una consulta periodicamente. Cada vez que se ejecuta una consulta programada en segundo plano, XDR crea una nueva consulta con el mismo nombre de consulta y el mismo ID de consulta, pero con un ID de ejecucion diferente.

2. Atributos de consulta: Las consultas ejecutadas se designan con columnas de clave denominadas atributos. Las columnas de clave (atributos) de las consultas ejecutadas que se muestran en la tabla del centro de consultas son las siguientes:
	- Query Name
	- Execution ID: Id generado cuando el query esta ejecutandose
	- Query ID: Generado cuando el query es creado
	- Query status: Como: Queued, running, failed, completed.
	- Num of results: El numero de las columnas en los resultados de tabla del query

3. Pagina de consultas programadas: Distinta de la pagina centro de consultas. Las consultas programadas solo contienen definiciones de consulta, como programacion, hora y proxima ejecucion de consultas. Ademas, la clave unica de las dos tablas es distinta. 
   Tipos de consultas programadas:
	- Consulta periodica programada
	- Consulta programada no periodica

	Atributos clave y acciones de las consultas programadas:
	- Hora programada: Frecuencia a la hora en la que se configuro la consulta para ejecutarse
	- Próxima ejecución: Muestra la hora de la próxima ejecución prevista.
	- Mostrar consultas ejecutadas#Nodo
