#Nodo

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
