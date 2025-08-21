#Nodo

1. Verdades vs mitos
	1. Mito: La busqueda de amenazas es una actividad que se realiza una sola vez, como un "sprint de busqueda" en una organizacion: 
	   Verdad: La búsqueda de amenazas es un esfuerzo continuo y deliberado para aprovechar las detecciones de baja fidelidad e identificar nuevas brechas de detección.
	2. Mito: La caza de amenazas no se puede gestionar ni medir, y en su mayoria no debe estar estructurada
	   Verdad: La búsqueda de amenazas es un proceso continuo de detección, ajuste y medición del retorno de la inversión (ROI). Esto no solo ayuda a descubrir amenazas, sino que también conduce a una gestión de detección más eficaz y a mejores prácticas.
	3. Mitos: La busqueda de amenazas es un sustituto de las alertas y la supervision
	   Verdad: La busqueda de amenazas es complementaria a las alertas y la supervision

2. La trifecta de deteccion: Caza, alerta y monitoreo: Al buscar amenazas, seleccione una metodología de detección basada en su fidelidad esperada. La fidelidad es la probabilidad de que un evento sea malo y requiera atención constante y en tiempo real.
   Mapa de fidelidad de deteccion de la busqueda, supervision y alertas desde la perspectiva del SCO de PAN
   
   - Alertas: Tasa de fidelidad de deteccion entre el 70 y 100 porciento y una tasa poco frecuente de falsos positivos. se realizan en tiempo real para escenarios especificos:
     - Volcado de credenciales mediante canalizaciones con nombre
     - Intentos de difusion de contraseñas a traves de ssh
 - Hunting / caza: Tasa de fidelidad de deteccion entre el 1 y 40% y una tasa frecuente de falsos positivos. Suele implicar esfuerzos semanales o quincenales centrados en la busqueda de conjuntos de datos que tienen una mayor probabilidad de tener amenazas. EJ.
	- Ejecuciones automaticas anomalas
	- servicios
	- familias especificas de malware como silver sparrow
	- Tecnicas especificas de recoleccion o volcado de credenciales
- Monitoring / Monitorizacion: Tasa de fidelidad de deteccion entre el 40 y 70% y una tasa periodica de falsos positivos. La supervision implica esfuerzos diarios o ejecuciones de un conjunto de amenazas potenciales como:
	- inicio de sesion fallidos de los usuarios
	- Inicio de sesion de escritorio remoto en servidores criticos dentro de su entorno

	Hunting activity happens in 5 steps:
	- inception
	- use case formation
	- toolset gathering
	- use case translation to signatures or data analytics
	- Hunting and investigating


3. Tres enfoques de la caza: Para buscar a lo largo del ciclo de vida de las amenazas ciberneticas
	1. Caza orientada a la tecnica: Puede realizar una búsqueda orientada a la técnica en función de las tácticas, técnicas y procedimientos enumerados en el marco ATT&CK MITRE. Cuando desarrolles hipótesis de caza, concéntrate en los comportamientos singulares de los atacantes que sean importantes para la caza. A continuación, seleccione las tácticas de ataque específicas que sean importantes y busque solo esas tácticas de ataque.
	2. Caza orientada a la familia de malware: Puede llevar a cabo una búsqueda orientada a la familia de malware en función de los comportamientos exhibidos por familias de malware específicas. En este enfoque, en lugar de elegir técnicas singulares, se eligen familias de malware más grandes, se obtienen sus indicadores de compromiso (IOC) y se buscan comportamientos específicos de esa familia de malware.
	3. Busqueda orientada a datos: En la búsqueda orientada a datos, la única hipótesis es buscar cualquier cosa "rara" o "anómala". En función del conjunto de datos más grande que tenga, busque especialmente cualquier cosa que pueda destacarse. Para ello, puede aprovechar algunas de las consultas XQL integradas en la biblioteca de consultas. También puede cazar a través de otros medios, como carreras automáticas y servicios.