CREACION DE CONSULTAS SENCILLAS
1. Investigacion de amenazas potenciales: se investigan a traves de la busqueda de amenazas
   LEAD: Primer contacto con una amenaza potencial, obtencion de un lead:
   - Alerta: Una alerta de un sistema que noe s PAN para endpoints o firewalls
   - Informacion sobre amenazas: informacion de amenazas bien definida de articulos en linea o inteligencia de amenazas externas
   - Usuarios / Endpoints: Usuarios o puntos de conexion que se han modificado o actuan de forma anomalo

	Alerta VS Lead 
	La alerta esta disponible al cliente, XDR detecta de forma precisa una alerta, por otro lado un LEAD puede convertirse en una alerta pero solo despues de que se haya definido.
	
	Threat hunting / Caza de amenazas
	Tambien llamada LEAD investigation, es cuando los analistas utilizan herramientoas de investigacion XDR para encontrar amenazas desconocidoas en conjuntos de datos XDR. Las herramientas deben utilizarse en el siguiente orden:
	- Query Builder: Busqueda de un LEAD usando Query Builder y determinar un sospecha, ataque dirigido.
	- Causality and Timeline: Investigar mas a fondo estos eventos usando Causality and Timeline para determinar el impacto en los recursos y atributos.
	- BOCs: Crea reglas XDR como Behavioral Indicator of Compromise (BIOCs) para crear alertas basadas en determinar atributos

2. Generador de consultas / Query Builder: Usado para buscar amenazas conocidas en conjuntos de datos XDR. Tenga en cuenta que la consola de administracion no proporciona una tabla dedicada a los registros.
   TIpos de consultas:
   - Consultas sencillas basadas en formularios: Puede crear consultas sencillas basadas en formularios seleccionando un tipo de entidad como archivo, proceso o registro y especificar criterios de busqueda en funcion de las propiedades de la entidad seleccionada.
   - Consultas XQL avanzadas: puede buscar cualquier atributo de registro disponible en los conjuntos de datos, asi como correlacionar registros mediante el lenguaje de consultas de XDR, XQL.
     
    Pagina del generador de consultas: Existen dos formas de crear consultas de busqueda:
    - Boton de busqueda de XQL, podemos escribir y ejecutar consultas XQL
    - Y en la enumeracion de los tipos de entidad para las consultas basadas en formularios.
	    - Los formularios contienen: Proceso, archivo, red y carga de imagen.

3. Formularios de consulta: Permite determinar el nombre de la consulta, las acciones, atributos de archivo, proceso del actor, ubicacion y hora de los tipos de entidad.

4. Acciones: Las acciones u operaciones se realizan en las entidades mediante procesos "actuantes" y estan disponibles para varios tipos de entidades.
   - Proceso de actuacion vs Proceso de accion: El distintivo es que un proceso debe ser victima de otro, es decir, Si el proceso P0 genera un proceso P1, el P0 es el actuador o proceso de actuacion y P1 es el proceso de accion.
   - Tipos de entidad: Proceso, archivo, registro, red.
   - Principales tipos de acciones:
	   - Proceso: Execution, injection
	   - File: create, read, rename, delete, write
	   - Registry: create_registry_key, delete_registry_key, rename_registry_key, delete_registry_value, set_registry_value

5. Opciones de ejecución: La consola de administración de XDR proporciona algunas opciones de ejecución diferentes para ejecutar una consulta.:
	- Correr: Puede ejecutar inmediatamente su consulta como una tarea en primer plano.
	- Ejecutar en segundo plano: Se puede ejecutar en segundo plano, cuando se completa la tarea en segundo plano se muestra una notificación.
	- Consulta programado: Se ejecuta una vez en un solo momento dado. 

6. Resultados de la ejecución de la consulta: Al ejecutar una consulta de búsqueda, independientemente del tipo XDR muestra los resultados de la ejecución den su pagina en una tabla denominada tabla de resultados.
   
   Tablas de resultados: 
   - Al igual que con otras tablas de la consola de administración, puede crear filtros en columnas, cambiar el diseño de la tabla, ocultar algunas columnas, exportar el contenido de la tabla y realizar acciones en una o mas filas de la tabla de resultados.
   - Las columnas y las acciones del menú contextual dependen del tipo de entidad de búsqueda especificada en la definición de consulta.
   - También puede abrir las vistas de causalidad o escala de tiempo para investigar mas a fondo.
   

ADMINISTRACION DE CONSULTAS
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
	- Mostrar consultas ejecutadas

