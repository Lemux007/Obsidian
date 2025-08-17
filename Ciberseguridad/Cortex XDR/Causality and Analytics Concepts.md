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

5. Acciones de alerta vinculadas: Proporciona acciones avanzadas de investigacion y visualizacion: Abrir tarjeta (Muestra toda la acadena de ejecucion del proceso que desencadeno la alerta en la vista de causalidad) y abrir linea de tiempo (Open timeline muestra las etapas del ciclo del ataque y todas las alertas, incluidas las alertas de gravedad informativa en la vista de cronograma)

6. Checkint stitching status / Comprobacion del estado de la costura: Puede comprobar el estado de la recopilación de registros y la vinculación de registros revisando los atributos de alerta que se muestran en el formato de notación de objetos JavaScript (JSON). con **Alt + clic derecho** para mostrar el menu de acciones y dar en "depurar alerta"


# CADENAS DE CAUSALIDAD
1. Region de ataque: Una región de ataque es un grupo de procesos en el árbol de procesos jerárquicos que están involucrados en un ataque. Uno de los desafíos que se presentan en este escenario es cómo distinguir qué procesos estuvieron involucrados en el ataque.

2. Instancias de causalidad: Las alertas vinculadas pueden revelar todos los procesos involucrados en actividades sospechosas. Una vez identificados los procesos responsables, sus operaciones sobre los recursos se pueden obtener fácilmente a partir de los datos mejorados del punto final
   ## Instancia de causalidad (CI)
   Cada grupo de procesos causalmente relacionados se denomina instancia de causalidad, o instancia de grupo de causalidad, Un objeto de instancia de causalidad puede incluir información sobre las interacciones proceso-recurso y las alertas, en función de la existencia de un ataque.
   ## Propietario del grupo de causalidad (CGO)
   En el caso de un ataque, el agente Cortex XDR termina todos los procesos en una instancia de causalidad, que se consideran responsables del ataque.

3. Formacion de instancias de causalidad: Cortex XDR proporciona una lista de procesos predefinidos y aprendidos conocidos como reproductores y desovadores finales. Ambos se actualizan a través de actualizaciones de contenido.
   - Desovadores: Para dividir el árbol de procesos en instancias de causalidad inconexas, el agente Cortex XDR utiliza procesos marcadores llamados generadores. Los procesos de generación son procesos especiales y aprendidos que el equipo de investigación identificó aprovechando las técnicas de aprendizaje automático (msiexec.exe, services.exe, winlogon.exe)
   - Generadores finales: Un solo ataque puede abarcar varias instancias de causalidad. Durante la investigación de amenazas, los generadores que pueden dar lugar a instancias de causalidad dependientes en un solo ataque también se identifican y agrupan bajo el nombre de generadores finales. (chrome.exe, firefox.exe, iexplore.exe)

# MOTOR DE ANALISIS
1. Analisis del comportamiento: El motor de análisis de Cortex XDR detecta y responde a las amenazas ocultas posteriores a la intrusión que han evadido las defensas de la red antes de que los ataques arruinen los sistemas.
   
   Proceso para detectar anomalias:
   1. Aprender el comportamiento normal
   2. Comparar las actividades con el comportamiento normal

2. Tacticas de MITRE Att&ck: El motor de análisis puede generar una alerta para cualquiera de las siguientes tácticas de ataque, tal como se define en las tácticas de MITRE ATT&CK.
   - Execution: Las tácticas de ejecución incluyen varias técnicas para ejecutar código malicioso en un punto final local o remoto después de obtener acceso a la red.
   - Persistence: Las tácticas de persistencia son técnicas para mantener el acceso en una red o en un punto final.
   - Discovery: Las tácticas de descubrimiento son técnicas aplicadas después de un acceso inicial para identificar más vulnerabilidades dentro de la red.
   - Lateral movement: Las tácticas de movimiento lateral son técnicas para expandir la huella dentro de la red, incluida la obtención de credenciales para obtener acceso adicional a más datos en la red.
   - Comand and control: Las tácticas de comando y control (C2) permiten a los atacantes emitir comandos de forma remota a un endpoint y recibir información de él.
   - Exfiltration: Las tácticas de exfiltración son técnicas para recibir información, como datos empresariales valiosos, de una red.

3. Cobertura del motor de analisis: El motor de análisis Cortex XDR proporciona una cobertura completa de las tácticas de ataque detectadas según lo definido por las tácticas MITRE ATT&CK.
   - Descubrimiento: El motor detecta tácticas de detección a través de una búsqueda de síntomas en el tráfico de red interna, como cambios en los patrones de conectividad que incluyen mayores tasas de conexiones, conexiones fallidas y análisis de puertos.
   - Movimiento lateral: El motor detecta tácticas de movimiento lateral mediante el examen de operaciones administrativas, como Secure Shell (SSH), Protocolo de escritorio remoto (RDP) y Protocolo de transferencia de hipertexto (HTTP), acceso a recursos compartidos de archivos y uso de credenciales de usuario que va más allá de lo normal para su red.
   - Comando y control: Detecta tacticas de comando y control a traves de una busqueda de cambios inexplicables en la periodicidad de las conexeiones.
   - Exfiltracion: El motor detecta tácticas de exfiltración mediante el examen de las conexiones salientes con un enfoque en el volumen de datos que se transfieren.

4. Ejemplos de alertas de Analytics y fuentes de datos utilizadas: Los tipos de alerta que puede generar el motor de análisis de Cortex XDR dependen de las fuentes de datos (fuentes de registro) que configure.

5. Componentes basicos del motor de analisis: Detectores de analisis, El motor de análisis organiza sus actividades de análisis de comportamiento por unidades llamadas detectores. Cada detector está especializado para tipos de ataque específicos y genera un tipo de alerta analítica cuando se detectan anomalías y comportamientos sospechosos.

6. Habilitacion de Cortex XDR Analytics: **Configuracion > Configuraciones > Cortex XDR - Analisis**
   Los datos recopilados de al menos 30 puntos de conexion deben estar disponibles en el almacenamiento durante al menos dos semanas
   El motor requiere un minimo de 5 dias de recopilacion.

