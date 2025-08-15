
DESCRIPCION GENERAL DE LAS REGLAS XDR
1. Reglas basadas en indicadores de amenazas personalizados: Se puede crear reglas propias XDR especificando la caracteristica de los indicadores de amenazas como criterios de regla. Para identificar los indicadores de amenazas es buscar clientes potenciales en los conjuntos de datos XDR. Alternativamente, los indicadores de amenazas se pueden obtener de flujos confiables de inteligencia de amenazas.
	1. Cortex comprueba el flujo de registros entrante con estas reglas, si hay coincidencia xdr genera alerta de deteccion con atributos como: nombre, categoria, gravedad.
	2. Cuando se genera un ataque y no se bloquea la alerta es de tipo deteccion, los ataques contra los puntos de enlace solo pueden ser bloqueados por el agente XDR, no por los componentes en la nube de las instancias XDR.

2. Tipos de reglas de CORTEX XDR: Existen reglas de XDR que podemos crear en funcion de la necesidad
	1. Indicadores de compromiso (IOC): Las reglas de IOC en cortex XDR definen las propiedades estaticas de las amenazas como nombres de archivo, rutas, hashes de archivos, ip y nombre de dopinio, su objetivo es detectar malware conocido y simple.
	2. Las reglas BIOC definen las caracteristicas de comportamiento de las amenazas, como las tacticas, tecnicas y procedimientos utilizados durante el ciclo de ataque, las reglas BIOC estan pensadas para detectar amenazas persistentes avanzadas, como ataques sin archivos.
	3. Reglas de correlacion: Deben considerarse como reglas BIOC muy avanzadas. De hecho la condicion de una regla de correlacion se define como una consulta de busqueda XQL. BIOC XQL es limitado en terminos de sintaxis XQL y conjuntos de datos disponibles, mientras que las reglas de correlacion pueden consistir en cualuier busqueda XQL que utilice casi cualquier sintaxis XQL para ejecutarse en varios conjuntos de datos.

3. Conjuntos de datos utilizados por el motor de reglas: La coincidencia de reglas se basa en dos componentes: La condicion de la regla y los flujos de registro entrantes almacenados en conjuntos de datos.
   - El motor de reglas XDR comprueba constantemente que los flujos de registro entrantres coincidan con las condiciones de la regla XDR
   - Algunos conjuntos de datos se crean para almacenar solo los registros creados por los componentes XDR, como los agentes XDR, otros se almacenan en registros de terceros.
   - Las reglas BIOC se comprueban con los conjuntos de datos xdr_data y cloud_audit_log, mientras que las de correlacion se comprueban en todos los conjuntos de datos.
   - El conjunto de datos xdr_data contiene registros y endpoints que se vinculara con registro de trafico NGFW si se proporciona la integracion



REGLAS DE IOC
1. Trabajar con los IOCs: Las reglas IOC estan destinaads a detectar malware simple y conocido. se crean en **Reglas de deteeccion > paginas de IOC**
   
   Acciones y atributos de IOCs
   - Indicador: El indicador es el valor del indicador, como el nombre de un archivo, una dirección IP o un valor hash.
   - Tipo: Tipo es el tipo del indicador de amenaza, como Ruta completa, Nombre de archivo, Dominio y Hash.
   - Fecha de caducidad: La fecha de caducidad es la fecha y la hora en las que el IOC se eliminará automáticamente de la instancia de Cortex XDR.
   - Reputación: La reputación es el nivel de confiabilidad de la regla del COI, que va desde **Completamente confiable** hasta **La confiabilidad no se puede juzgar**.


REGLAS BIOC
1. Trabajar con BIOCs: Las reglas de BIOC estan pensadas para detectar amenazas avanzadas en funcion de las caracteristicas del comportamiento.
   Crear y administrar reglas BIOC: Reglas de deteccion > bioc en la consola de administracion.
   
   Metodos para obtener reglas BIOC:
   1. Reglas de importacion: Puede importar reglas BIOC desde un archivo que se creo exportando las reglas de BIOC desde otra instancia de cortex XDR, click en **import rules**
   2. Ademas de las reglas BIOC definidas por el usuario, el equipo de investigacion de PAN ccrea reglas BIOC y las distribuye a todas las instancias de Cortex XDR a traves de las actualiazciones de contenido. Conocidas como reglas BIOC globales.

	Atributos clave de BIOC:
![[Pasted image 20241209120240.png]]
	Acciones sobre las reglas BIOC:
		![[Pasted image 20241209120645.png]]

ADICION DE UNA REGLA BIOC: Consta de dos pasos
1. **Definir la condición de la regla y establecer un nombre de regla**: Definira la condicion de regla que consta de indicadores de amenaza y un nombre de regla BIOC. Definir una condicion regla BIOC es lo mismo que crear una busqueda de consulta, solo que BIOC genera alerta. 
   
   En la consola de admin hacer clic en **+Agregar BIOC**, se presentaran dos opciones para especificar la concicion de la regla: Usar XQL search o usar consultas de busqeda basadas en formularios.
   
   USO de busqueda XQL: Puede utilizar la busqueda XQL para definir las condiciones de las reglas BIOC, tega en cuenta las limitaciones:
   - No se puede utilizar toda la sintaxis XQL en BIOC XQL
   - Solo dos conjuntos de datos XDR_data y cloud_audit_log, estan disponibles para BIOC XQL.
    
    BIOCs basados en formularios: Otra forma es seleccionar un tipo de recurso de la lista poporcionada e introducir los parametros de busqueda relacionados. Tipos de entidades: Proceso, archivo, red, Carga de imagen y registro.
    
	Tipo de archivo: Formulario BIOC
	![[Pasted image 20241209121611.png]]

2. **Especificar otros parametros de regla**: Se especifican los parametros de regla restantes relacionados con alertas, gravedad y el tipo, que generaran alertas si se encuentran en una coicidencia de regla. ![[Pasted image 20241209121950.png]]


REGLAS DE PREVENCION PERSONALIZADAS
1. Descripcion general de las reglas de prevencion personalizadas: Son reglas BIOC que se transfieren a los endpoints mediante perfiles de restriccion.
   Funcionalidad: Permite a los agentes bloquear actividades que coinciden con los criterios de la regla.
   Capacidad: Para transportar las reglas BIOC deseadas a los agentes en forma de reglas de proteccion contra amenazas conductuales (BTP), las reglas de prevencion personalizadas sutilizan perfiles de restricciones.

2. Creacion de reglas de prevencion personalizadas
	1. Habilitar reglas de prevencion personalizadas en los perfiles de restriccion: No seleccionar ninguna regla BIOC, en su lugar prepare uno de los perfiles de restricciones para transferir las reglas BIOC seleccionadas en los puntos de conexion custom **preevention rules > Action mode > enabled > marcar: auto-disable rules > times in 30**
	2. Agregar al perfil de restricciones desde el menu contextual de una regla: Busque la regla BIOC deseada en la tabla y a continuacion, haga clic en agregar al perfil de restricciones en el menu contextual. Esta accion abre un cuadro de dialogo en el que se puede seleccionar el perfil de restricciones que habilito anteriormente. despues damos en clic **Agregar**, la regla BIOC se asocia con el perfil de restricciones solicitado

REGLAS DE SUPRESION DE IOC / BIOC
1. Creacion de reglas de supresion: Puede crear una regla de IOC o BIOC para definir las condiciones en las que no se debe de coincidir **Configuracion > Configuraciones de expceciones**. Anuque puede deshabilitar una regla IOC  o BIOC directamente desde el menu contextual
   
   **Creacion de regla de supresion**: 
   Hay algunos pasos en la creacion de reglas de supresion desde **Configuracion de expcepciones > Reglas de supresion de IOC/BIOC**, proporcionar nombre de regla, condiciones de regla, definir criterios de regla, hasg, nombre, ruta, autoridad bajo la que se ejecuta. Ambito de regla, ya sea que la regla de supresion se aplique a IOC, BIOC o ambos.
