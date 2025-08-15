
MODULOS DE SEGURIDAD (Nuevo modulo de seguridad de proteccion del servidor de informacion de internet IIS para cortex XDR)

Protección IIS
	Protetege contra las amenazas dirigidas l IIS. y cortex XDR proporciona proteccion de shellcode en proceso para procwesos de windows de 32 bits.
	Para cambiar esta configuración, vaya a Endpoints > Policy Management > Prevention > Profiles > Malware > Información general > IIS Protection.



MEJORAS EN LAS MAQUINAS VIRTUALES DE BROKER
1. Cluester de alta disponibilidad para maquina virtual de agente
	Para garantizar la alta disponibilidad HA en la prestacion de servicios que se ejecutan en la VM del agente cortex XDR incluye un cluster de alta disponibilidad de la maquina virtual del agente.

2. Requisitos previos para crear un cluster de VM de broker
	1. Un modo operativo: Para que el cluster comience a funcionar y proporcionar servicios, se necesita al menos un nodo operativo.
	2. Pathfinder desactivado
	3. Redesignaicion de corredor: Cambiar rol designado actual de la VM del agente.

3. Ajustes y configuración
	1. Capacidad ampliada: Cada applet de agente local en la VM admite hasta 50,000 agentes en lugar de solo 10k anteriores
	2. Importacion de configuracion de VM de Broker: Se puede importar configuracion.


MEJORAS EN LA AUTOMATIZACION DE CORTEX XDR
1. Mejoras en la automatizacion: Se agregaron acciones adicionales con la respuesta de los endpointes y el analisis forense, umbrales configurabels flexibles, con opcion para indicar a traves de correo electronico o slack. **Configuración > Configuraciones > Configuración de automatización**.


CAPACIDADES DEL PERFIL DE SEGURIDAD CONTRA MALWARE PARA MacOS
1. Simplemente el modulo de seguridad Examen de amenazas de archivos locales ya esta disponible en macOS, proporcionando adicionalmente poner en cuarentena archivos malintencionados y procesos malintencionados para el edp.


APLICACIONES DE LAS NORMAS BIOC A LA PREVENCION
	Las reglas BIOC proporcionaban deteccion y prevencion simultaneamente y ahora se pueden separar.
1. Administracion de la prevencion por separado de las detecciones: Para proporcionarle mas granularidad, Cortex XDR ahora le permite administrar la deteccion por separado de la prevencion al deshabilitar una regla BIOC.
	1. Identificar una regla BIOC: Comience por identificar una regla BIOC vinculada a un perfil de prevención.
	2. Desactivar compontentes BIOC: Vaya a **Reglas de detección > BIOC** y seleccione el BIOC identificado anteriormente vinculado a un perfil de prevención. Haga clic con el botón derecho en la regla BIOC y haga clic en **Deshabilitar**. Aparecerá una ventana emergente con dos opciones.
	3. Deshabilitacion de un agente o un servidor: AL deshabilitar el agente se deshabilitara parcialmente la regla al eliminar la prevencion y las capacidades de deteccion se quedan en el servidor.  Al deshabilitar el servvidor tambien se deshabilitara parcialmente la regla.  La mejor practica es ingresar una nota con respecto al motivo de la deshabilitacion.

MEJORAS EN EL AISLAMIENTO DE AGENTES (LINUX)
1. Aislamiento de agentes: Ahora puede cancelar la opcion de aislar un agente si la conexion con el servidor administrador ha perdido la conexion despues de un periodo de tiempo. La configuración se encuentra en **Configuración del agente: Linux > Revert Endpoint Isolation.**


ADICIONES DE XQL (Cortex Query Language)
1. Funcion XQL para ordenar campos por popularidad: Ahora admite una funcion de orden de columnas con la etapa de vista, usada al crear una consulta y desee mostrar los resultados que contienen campos vacions con un valor nulo en el ultimo lugar.
2. Etapa getrole de XQL para enriquecer eventos con roles especificos: Para mejorar las capacidades de investigacion. Enriqueciendo los eventos con roles especificos asociados con nombres de usuario o puntos de conexion.