# DESCRIPCION GENERAL DE LAS ACCIONES DE RESPUESTA
1. Acciones de Cortex XDR:
	1. Respuesta instantanea: Responde inmediatamente a las actividades maliciosas en un endpoint poniendo en cuarentena el archivo o finalizando un proceso
	2. investigaciones adicionales: Podemos ir a live terminal para buscar mas a fondo.
	3. Mantenimiento y administracion: Desinstalacion o actualizacion de los agentes.
	   
	   Objetivos: 
	   - Procesos y archivos: Acciones como poner en cuarentena un archivo en cuarentena
	   - Endpoints
	   - Redes

2. Inicio de acciones en la consola de administración: Se conocen distintas maneras:
	1. Desde la pagina del centro de actividades: Vaya a **Respuesta a incidentes > Centro de actividades > +Nueva** acción y elija la acción que desea realizar.
	2. Desde el menu contextual
	3. Desde el menu lateral: Para iniciar Live Terminal directamente desde el menú de la barra lateral, vaya a **Respuesta a incidentes** **> Live Terminal**.
3. Acciones iniciadas por el servidor: Cortex XDR usa WebSocket para enviar acciones a los agentes de Cortex XDR, lo que tiene más ventajas en comparación con el protocolo HTTP. Caracteristicas: 
   - Velocidad
   - Sesiones en vivo
   - Conmutacion por error a la opcion HTTP

4. Limitar el acceso a las acciones: Puede restringir el acceso a las acciones que los usuarios pueden realizar en la consola de administración mediante roles XDR.
   Para acceder a las funciones de Cortex XDR para la instancia actual, vaya a **Configuración de configuraciones de > > Funciones de > de administración de acceso**. Haga clic en la imagen para ampliarla.
   Para verificar su rol, haga clic en su nombre de usuario de CSP y haga clic en **Acerca de**. Haga clic en la imagen para ampliarla.


# CENTRO DE ACTIVIDADES
1. Inicio de acciones en el centro: El centro de actividades hospeda lista de objetos modificados por las acciones completadas correctamente, como la lista de los archivos en cuarentena, la lista de los archivos bloqueados y permitidos y la lista de extremos aislados.
   Acciones:
   - Iniciar nuevas acciones
   - Seguimiento de nuevas acciones
   - Acceso a las acciones aplicadas actualmente
   - Acceso a la biblioteca de scripts del agente
   - Acciones de archivado

2. Acciones en el centro de actividades: 
   ![[Pasted image 20241211114140.png]]

3. Estado de las acciones de seguimiento: Puede realizar un seguimiento del estado de las acciones en la columna Estado de la tabla y todas las acciones
   - Pendiente
   - En curso
   - Caducado
   - Cancelado
   - Completado con exito
   - Completado con exito parcial
   - Fracasado

4. Acciones de seguimiento: Puede revertir una accion ya realizada desde el menu contextual: Restaurar, Rerun, Mover a lista de permitidos, cancelar el aislamiento de puntos de conexion.

5. Anulacion de hash de lista de bloqueo: Permite definir una configuracion opcional para terminar hashes en un endpoint, independientemente de la configuracion del perfil de malware


# ACCIONES DE RESPUESTA DE ENDPOINTS
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
    Para deshabilitar las capacidades de un endpoint, vaya a **Endpoint Control > Disable Capabilities.**