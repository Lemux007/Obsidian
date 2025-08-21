#Nodo

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