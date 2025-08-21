#subindex 

# Log stitching / costura de troncos
1. Alertas y registros: Hay dos tipos de datos que se envian a una instancia de XDR
	1. Alertas: Las alertas se crean instantáneamente para capturar detalles de actividades sospechosas y se cargan inmediatamente en una instancia de Cortex XDR. Sin embargo, la rápida creación y procesamiento de una alerta no le permite capturar detalles de todas las actividades. Por ejemplo, una alerta no puede contener interacciones proceso-recurso; por lo tanto, no es útil para el análisis de amenazas conductuales por sí solo
	2. Registros: Los registros pueden ser cualquier dato, no necesariamente información relacionada con ataques. Los registros se cargan periódicamente en la instancia de Cortex XDR. A menos que se asocien con alertas, los registros por sí solos no proporcionan suficiente información para el análisis del comportamiento. Entre los ejemplos de tipos de registro se incluyen los datos de punto de conexión mejorados creados por el agente XDR, los registros de tráfico del firewall y los registros de autenticación.

2. Alertas correlacionadas con registros: Cortex XDR puede correlacionar alertas y registros, lo que también se conoce como unión de registros. Este proceso de combinación da como resultado alertas mejoradas con más atributos (campos) que contienen información sobre los detalles del ataque. El analisis de una alerta vinculada puede revelar:
   - Cadenas de causalidad: XDR puede regnerar informacion de causalidad que muestra las interacciones proceso - recurso relacionadas con el taque en graficos causales jerarquicos.
   - Cronologia: XDR puede mostrar la linea de tiempo de cuando se invocaron esas ejecuciones de procesos relacionadas con ataques.

3. Recopilacion de datos de endpoints mejorada: Los agentes de Cortex XDR Pro Endpoints, también conocidos como Pro Agents, pueden recopilar registros mejorados de datos de endpoints (EED) en endpoints. El agente XDR también realiza estas tareas continuas, como la supervisión del sistema operativo (SO), el muestreo de datos, la recopilación (almacenamiento local), la compresión y la carga.
   
   Contenido del registro EED, Los datos de punto de conexion mejorados incluyen estos tipos de registro:
   - Operaciones de proceso en recursos del SO como archivos, procesos, redes, registro.
   - Registro de eventos de windows
    Como se accede a los registros? Por consultas de busqueda mediante el generador de consultas de la consola de administracion o usar XQL

4. Alertas vinculadas en la tabla de alertas: Puede identificar las alertas vinculadas en la tabla Alertas comprobando uno de los atributos de alerta relacionados con la causalidad, como Nombre de CGO y Firmante de CGO. También está el atributo Id. de causalidad (CID) que muestra el estado de unión.
   ![[Pasted image 20241210094759.png]]

5. Acciones de alerta vinculadas: Proporciona acciones avanzadas de investigación y visualización: Abrir tarjeta (Muestra toda la cadena de ejecución del proceso que desencadeno la alerta en la vista de causalidad) y abrir linea de tiempo (Open timeline muestra las etapas del ciclo del ataque y todas las alertas, incluidas las alertas de gravedad informativa en la vista de cronograma)

6. Checkint stitching status / Comprobacion del estado de la costura: Puede comprobar el estado de la recopilación de registros y la vinculación de registros revisando los atributos de alerta que se muestran en el formato de notación de objetos JavaScript (JSON). con **Alt + clic derecho** para mostrar el menu de acciones y dar en "depurar alerta"
[[Cadenas de causalidad]]
