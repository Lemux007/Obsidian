#Nodo

1. Acciones de respuesta de aislamiento y cancelacion de puntos de conexion de aislamiento: 
   #### Aislamiento de un punto de conexión
   Puede utilizar el menú contextual de un punto de conexión para iniciar la acción de aislamiento en el punto de conexión. El punto de conexión está completamente aislado del resto de la red cuando esta acción se completa con éxito. Sin embargo, el agente aún puede conectarse a la instancia de Cortex XDR.
   #### Permitir procesos en un punto de conexión aislado
   Todavía puede permitir que algunos procesos de un punto de conexión aislado se conecten a algunas direcciones IPv4 o IPv6 específicas mediante la configuración Acciones de respuesta en el perfil de configuración del agente aplicado. Para cada entrada de la lista de permitidos, especifique los nombres de los procesos, posiblemente con comodines (*) y direcciones IPv4 o IPv6.
   #### Cancelación del aislamiento de puntos de conexión
   Puede cancelar un aislamiento de dos maneras: utilizando la acción Cancelar aislamiento de punto final del Centro de actividades, como se muestra en el ejemplo, o utilizando la aplicación Cytool con la opción de comando **de parada de aislamiento**.

2. Accion de respuesta de terminal en vivo: Proporciona 4 interfaces
   - Administrador de tareas
   - Explorador de archivos
   - Linea de comandos
   - Python
     
    Coretx XDR le permite desactivar las capacidades de los endpoints como live terminal, recuperacion de archivos y ejecucion de scripts, desde su menu contextual.
    Para deshabilitar las capacidades de un endpoint, vaya a **Endpoint Control > Disable Capabilities.**#Nodo
