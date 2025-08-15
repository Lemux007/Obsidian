OBJETOS, ATRIBUTOS Y ACCIONES DE ALERTA
1. Objetos relacionados con alertas: Al analizar una alerta, puede comprender mejor la causa de lo que sucedio en contexto para valida si una alerta requiere accion adicional
   - Comun a todos los tipos de licencia:
     - Alerta
     - Incidente
     - Registro
   - Disponible en licencias pro:
	 - Alertas cosidas: o Stitched, son alertas mejoradas por cortex XDR que se correlacionan automaticamente con los registros para proporcionar una mejor visibilidad.
	 - Propietario del grupo de caausalidad (CGO): CGO es el proceso identificado como causa raiz de un ataque
	 - Punto de vista de causalidad: Esta vista es el nombre de una pagina de la consola de administracion especializada en el analisis de causalidad de alertas.

2. Trabajar con alertas: La consola de admin muestra alertas en la tabla de Alertas. Puede acceder desde **Respuesta a incidentes > Incidentes > Tabla de alertas** o introduciendo la URL **/alerts**

3. Atributos de clave de alerta: ![[Pasted image 20241209145719.png]]
	Descripciones de atributos de alerta:
	![[Pasted image 20241209145754.png]]
	Atributo de ID externo: El origen de la alerta genera el ID externo de una alerta; por lo tanto, este atributo es externo a la instancia de Cortex XDR. La columna ID externo esta oculta de forma predeterminada.
	EN caso de que el origen sea el agente de XDR, este ID se conoce como ID de prevencion.

3. Atributos de alerta en JSON: Puede obtener informacion mas detallada y especifica de los atributos de una alerta revisando los valores de sus atributos.

4. Acciones sobre alertas: El menu contextual de una alerta muestra las acciones aplicables, cuya disponibilidad varia en funcion del origen y categoria de la alerta y de si la alerta se vinculo con los datos del punto final.
	1. Investigar la cadena de causalidad: Tiene opciones para abrir la alerta en la vista de causalidad
	2. Administrar alerta: En administrar alerta, puede seleccionar **Crear excepcion de alerta** para poner la regla que hizo que el agente de XDR activara la alerta en modo silenciosos para que no desencadene alertas.
	3. Recuperar datos adicionales:
	   - Recuperar datos de alerta
	   - Recuperar archivos relacionados
	4. Pivota a vistas: Ver detalles complementos de endpoints para abrir el endpoint en el que se produjo la alerta.


REGLAS DE ALERT STARRING
1. Alertas destacadas: Es una regla para destacar y priorizar una alerta. Prioriza sus incidentes de alojamiento.

2. Creacion de nuevas alertas starring rule: Para crear una nueva alerta destacadaa, vaya a **Respuesta a incidentes > Configuracion de incidentes > Alertas destacadas** > **Agregar configuracion de estrella**


CAMPOS DE ALERTA DESTACADOS
1. Descripción general de los campos de alerta destacados: Utilizados para localizar y priorizar fácilmente las alertas con valores específicos de alerta destacados 
   Funcionalidad: Los campos de alerta destacados proporcionan una funcionalidad similar al filtrado en la tabla Alertas. Considere lo difícil que seria crear criterios de filtro para una lista de 100 nombres de host.
   Modo de empleo: Para beneficiarse de esta caracteristica, primero agregue nuevos valores de campo destacado a cualquiera de los campos de alerta destacados y a continuacion ordene o filtre la tabla de alertas en lo scampos de alerta proporcionados

2. Priorizar las alertas que contienen valores destacados: Despues de agregar valores especificos a los campos destacados, priorica las alertas que contengan valores de campos en la tabla alertas campos: Nombre de alerta, Contiene host destacado, contiene usuario destacado y contiene direccion ip destacada

3. Agregar nuevos valores de campo destacado: vaya a **Respuesta a incidentes > Configuracion de incidentes > Campos destacados** y haga clic en una de las opciones de valor destacado disponibles: Hosts, usuarios, direcciones IP y directorio activo.

4. Cambiar manualmente el estado y la gravedad de las alertas y los incidentes: Podemos cambiar el estado y gravedad de una alerta o incidente haciendo clicl derecho en una alerta y seleccionar Cambiar estado o cambiar gravedad.. y el estado de un incidente o alerta en: Nuevo, en investigacion y resuelto.