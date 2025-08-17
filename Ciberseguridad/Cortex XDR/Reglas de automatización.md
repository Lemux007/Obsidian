# CREACION DE REGLAS DE AUTOMATIZACION
1. Condiciones de la regla de automatizacion: Las reglas de automatización proporcionan un mecanismo para automatizar las respuestas a las alertas. Las reglas de automatización tienen condiciones y acciones. Más concretamente, las reglas de automatización de Cortex XDR permiten definir condiciones de alerta que desencadenan una acción.

2. Categorias de accion de reglas de automatizacion: Al especificar la accion de una regla de automatizacion, puede elegir entre 3 categorias de accion:
	1. Comunicacion: Optar por enviar un correo, mensaje de slack o realizar el envio de syslog
	2. Getion de alertas e incidentes: Puede asignar un incidente a un analista, establecer la rgavedad de la alerta. o establecer el estado de la alerta.
	3. Respuesta del punto de conexion: Puede optar por aislar el iniciador de alertas o el host remoto de alertas.

3. Reglas de automatizacion, SBAC y etiquetas de punto de conexion: Las reglas de automatización admiten el control de acceso basado en ámbitos (SBAC). SBAC le permite controlar quién puede hacer qué con las reglas de automatización mediante etiquetas de punto final. Una etiqueta de punto de conexión es un elemento dinámico que se puede crear y asignar a uno o varios puntos de conexión. Mediante el uso de etiquetas de punto de conexión, puede segmentar los puntos de conexión en varias capas. Una vez asignada una etiqueta de punto de conexión, puede usarla para establecer grupos de puntos de conexión, políticas y acciones.

	Factores a tomar en cuenta al editar en cuenta al editar una regla:
	- Permisos en modo restrictivo: Si el acceso al servidor esta habiltado y esablecido en restrictivo, puede editar una regla si tiene ambito para todas las etiquetas de regla
	- Permisos en modo permisivo: Puede editar una regla si tiene ambito de al menos una etiquet enumerada en la regla
	- Cambiar el orden de las reglas: Debe tener permisos para las otras reglas para las que desea cambiar el orden
	- Permiso de solo lectura: 
	- Si se agrego una regla cuando se establecio en modo restrictivo y luego se cambio a permisivo.


# GESTION DE REGLAS DE AUTOMATIZACION
1. Registro de auditoria de automatizacion: El registro de auditoría de automatización muestra todos los registros de todas las ejecuciones de reglas de automatización, incluidas las acciones correctas, fallidas y en pausa.
   **Ver alerta desencadenante** > **Ver el centro de actividades**
   