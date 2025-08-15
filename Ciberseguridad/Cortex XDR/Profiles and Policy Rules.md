PERFILES
1. Pagina de administracion de politicas: Desde endpoint>>Policy Managment, XDR ofrece 3 secciones para administrar reglas y politicas:
	![[Pasted image 20241203095956.png]]
2. Perfiles de prevención predeterminados: XDR proporciona un perfil predeterminado para cada tipo de perfil con el fin de iniciar de inmediato la protección de los terminales. ![[Pasted image 20241203100606.png]] 
	1. Agent Settings: Contiene configuraciones que especifican como funcionan normalmente los agentes de XDR, como limites en el espacio de registro en los terminales, hailitar la recopilacion mejorada de datos terminales EED o establecer una nueva contraseña de supervisor.
	2. Exploit: Este perfil puede bloquear fallas del sistema en los navegadores como kits de exploits.
	3. Malware: Deshabilita las cargas de archivos en wildfire o habilitar la cuarentena de los mismos.
	4. Restricciones: Puede bloquar intentos de ejecutar archivos desde uan USB o capertas desconocidas
	5. Exceptions: Deshabilitacion de modulos de proteccione contra vulnerabilidades de seguridad para un proceso especifico que se habilito globalmente en un perfil de vulnerabilidad. 
3. Gestion de perfiles de prevencion, importar y exportar un perfil desde los puntos de conexion > administracion de politicas > perfiles > prevencion


REGLAS DE POLITICA
1. Las reglas de directiva se utilizan para asociar perfiles a los endpoints., los perfifles asociados a una regla se consideran como la carga de una regla de politica para transmitirla a los puntos de conexion de destino.
	1. Componentes de la regla directiva: nombre de regla unico, lista especifica de puntos de conexion y lista de perfiles con un perfil para cada tipo de perfil admitido.
	2. Orden de las reglas: El orden es importante porque XDR evalua las reglas de arriba a abajo y la primer regla se aplica como la regla de politica activa.

2. Reglas de directiva predeterminadas: lista para usar todos los terminales registrados con una regla de politica predeterminada por plataforma.
3. Creacion de reglas de directiva: **Endpoints > Policy Management > Prevention > Policy Rules** Damos click en +Agregar directiva y seleccionamos Crear nueva
	1. Generalidades: Especificar: Nombre de directiva, platforma, seleccionar los perfiles creados anteriormente para cada tipo de perfil. 
	2. Objetivo: Se especifica el ambito o cobertura de la regla en forma de puntos de conexion de destino mediante filtros o seleccionando los edps manualmente.
	3. Resumen: De las especificaciones, dar listo.
	4. Guardar: Una vez agregada la regla de directiva en la tabla de reglas de directiva de prevencion, damos en guardar.


PERFILES DE CONFIGURACION DE AGENTES
	El perfil contiene ajustes que afectan al funcionamiento de los agentes de Cortex XDR en los terminales.
1. Configuracion del agente para puntos de conexion de windows
	1. ![[Pasted image 20241203113942.png]]
	2. ![[Pasted image 20241203114000.png]]
2. Si la proteccion conrta manipulacion del agente XDR esta habilitada puede refinar las siguientes opciones:
	1. Proteccion del servicio
	2. Proteccion de procesos Cyberserver.exe Cytrat.exe CyveraConsole.exe
	3. Proteccion de archivos de ruta: (%PROGRAMFILES%\Palo Alto Networks\Traps) y la carpeta de datos (%PROGRAMDATA%\Cyvera).
	4. Proteccion del registro: Protege claves y valores del registro de agente Cortex XDR almacenados en HKLM\SYSTEM\Cyvera
3. Terminales XDR Pro: Utilizar los perfiles de configuracion del agente para determinar que tipo de licencia adquieren los endpoints
4. Config global y especifica del agente: Hay dos tipos de configuraciones de agente: Exclusivas de un sistema operativo/punto de conexion especifoco y las configuraciones globales del agente. Esta ultima cubre 3 areas principales:
	1. Contraseña de desinstalacion global
	2. Gestion de contenidos
	3. Actualizacion de agente



PERFILES DE RESTRICCIONES
1. Opciones de configuracion de perfil de restricciones: Los perfiles de restricciones limitan la superficie expuesta a ataques en los puntos de conexion de windows defiendiendo donde y como los usuarios pueden ejecutar archivos. Opciones de condiguracion de perfil de restricciones:
	1. Archivos ejecutables
	2. Archivos de ubicacion de red
	3. Archivos multimedia extraibles
	4. Archivos de unidad optica
	5. Reglas de prevencion personalizadas
2. restricciones en archivos ejecutables: Si usamos archivos ejecutables para limitar la ejecucion de los archivos en los discos duros, especificaremos la siguiente configuracion.
	1. Modo de accion: Especifica la ccion realizada por XDR cuando se cumplen los criterios supervisados proporcionados en este grupo.
	2. Uso predeterminado: **marcar: Use Default** Si desea utilizar la accion predeterminada para el grupo de configuraciones
	3. Archivos/Carpetas en lista de bloque: Podemos especificar la lista a bloquear.
3. Implementacion de modo de accion por parte del agente.
	1. ![[Pasted image 20241203120353.png]]
4. Restriccion en archivos ejecutables para discos no HDD: Se pueden configurar: ARchivos de ubicacion de red, archivos de medios extraibles, archivos de unidad optica. ![[Pasted image 20241203120713.png]]

