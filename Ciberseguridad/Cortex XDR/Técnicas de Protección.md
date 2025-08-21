#Nodo

   Aleatorizacion del diseño del espacio de direcciones (ASLR)
	- Componentes colocados aleatoriamente: Componentes de procesos: Las ubicaciones de pila, monton y las bibliotecas se colocan aleatoriamente en cada ejecucion. Esto basado en la suposicion de que los componentes estan en una ubicacion conocida, fallara.
	  El espacio de direcciones virtuales continuo y no fragmentado de un proceso proporciona oportunidades a los atacantes en el sentido de que los atacantes pueden predecir la ubicación de las instrucciones de máquina reutilizables (MI) y de las regiones de pila y montón.
	  El ROP se basa en la creación de una pila falsa y en la identificación de los MIs reutilizables ya cargados en la memoria del proceso.
 ![[Pasted image 20241204132404.png]]



MODULOS DE PROTECCION CONTRA EXPLOITS
1. Caracteristicas de los modulos de proteccion contra exploits (EPM)
	1. Numeros equivalentes: un EPM de XDR bloquea tecnicas de explotacion concretas proporcionando numeros equivalente de EPM al numero de tecnicas de explotacion
	2. Perfiles de exploits: Puede crear perfiles de exploits para determianr que grupo de EPM esta activo para que procesos
	3. Vacunas selectivas
	4. EPM es analogo a la vacunacion contra un virus en particular, los procesos y los nucleos se vacunan selectivamente
	5. Proteccion de aplicaciones frente a kernels: El agente inyecta EPM en los procesos, mientras que el agente utiliza controladores de kernel contra las vulnerabilidades del kernel.
	Bloqueo EPM ![[Pasted image 20241204132947.png]]
	LISTA DE MODULOS DE PROTECCION CONTRA EXPLOITS
	- Proteccion APC: evita ataques que cambian el orden de ejecucion de un proceso mediante una llamada a procedimiento asincrono (APC)
	- Proteccion contra fuerza bruta: evita que los ataques de fuerza bruta secuestren el control del flujo del proceso mediante el uso de capas de proteccion del sistema operativo integradas, como ASLR
	- Prevencion de ejecucion de datos (DEP): DEP impide que las areas de memoria designadas que contienen datos se ejecuten como codigo.
	- Seguridad de DLL: impide acceso a metadatos cruciales de DLL desde ubicaciones de desconfianza
	- Explit Kit Fingerprint: Usada en kits de exploits de navegador para identificar informacion como el SO o aplicaciones que se ejecutan en un edp
	- Mitigacion JIT: Evita que un atacante omita las mitigaciones de una memoria del SO mediante motores de compilacion Just in Time (JIT)
	- Proteccion de escalada de privilegios de kernel: Evita que un atacante use el privilegio de otro proceso con mayores privilegios para ejecutar un proceso con permiso del sistema
	- Mitigacion de ROP: Protege contra ROP a las API utilizadas en las cadenas de ROP
	- UASLR: Mejora o implementa por completo ASLR con mayor entropia, robustez y aplicacion estricta.
	
Flujo de prevencion de exploits
	![[Pasted image 20241204134040.png]]
	

PERFILES DE EXPLOITS
- Contienen grupos de config para evitar amenazas que aprovechen vulnerabilidades o fallos en SW
- Controlan que EPM estab habilitados en que procesos y kernels
- XDR No permite la habilitacion de un EPM en particular.
- Agrupan funcionalmente los EPM en secciones por tipo de componente vulnerable en el endpoint

	Vulnerabilidades de endpoints: SO, bibliotecas, mecanismos de carga, aplicaciones conocidas, navegadores, protocolos de navegacion, aplicaciones personalizadas.
	Tablas de secciones de perfil de exploit: ![[Pasted image 20241204135614.png]]

	Aprovechar las secciones de la pagina de perfil
	- Proteccion contra exploits del navegador: opera o iexplore.exe
	- Proteccion de procesos vulnerables conocidos excel.exe, word.exe, cmd.exe
	- Proteccion contra vulnerabilidades del SO spoolsv.exe o svchost.exe
	- Proteccion de vulnerabilidades logicas (Protege de los ataques que aprovechan los mecanismos del SO y carga de DLL)
	- Proteccion contra exploits para procesos adicionales (Protege aplicaciones desarrolladas internamente de los ataques de vulnerabilidades)


TRABAJAR CON PROCESOS PROTEGIDOS
1. DLL inyectadas: Process Explorer Sysinternals Suite obtiene una lista de archivos dll inyectados por cortex XDR
2. Obtener lista de procesos protegidos: Se usa aplicacion Cytool con la opcion de enumeracion para obtener la lista actual de procesos protegidos en endpoint pero no muestra los nombres solo los PID o id del procesos.
3. Controladores del kernel Cortex XDR: Encargado de tareas de bajo nivel: administracion de tablas de politicas, inyecciones, prevenciones, proteccion del servicio y supervision del sistema de archivos.  **driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-object**
4. Desactivacion de EPM: Crear una excepcion de proceso para deshabilitar las EPM seleccionadas en un proceso
   ![[Pasted image 20241204170934.png]]
