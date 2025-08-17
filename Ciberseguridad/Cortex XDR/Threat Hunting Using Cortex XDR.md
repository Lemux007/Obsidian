# METODOLOGIAS DE BUSQUEDA DE AMENAZAS

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

-----
# CAZA ORIENTADA A LA TECNICA
1. Metodologia "shift-Right": La metodologia de desplazamiento a la derecha se centra aun mas en el ciclo de vida de un ataque, donde es mas escencial cazar. El atacante avanza de izquierda a derecha, comenzando con un reconocimiento general del entorno objetivo hasta la militarizacion y la entrega de malware, ya sea a traves de phishing u otros medios.
   
   - Reconocimiento, armamentizacion, entrega: Estas etapas del ataque implican
     - Acceso inicial, descubrimiento, evasion de la defensa, ejecucion
   - Explotacion, instalacion, mando y control, acciones sobre objetivos: Estas etapas del ataque implican
     - Escalada de privilegios, persistencia, mando y control, movimiento lateral, coleccion, acceso a credenciales, exfiltracion
       La caza de amenazas se realiza en estas etapas del ataque.

2. Ejemplo de reglas BIOC en cortex XDR: Varios BIOC vienen listos para usar con cortex XDR. Estos BIOC buscan tacticas, tecnicas y procedimientos especificos y cada uno de ellos se asigna a la categoria MITER ATT&CK o a la tactica MITER ATT&CK
   - Proceso de microsoft office que genera un proceso del que se abusa con frecuencia (Categoria: ejecucion)
   - Adobe Acrobat REader colocacion de un archivo ejecutable en el disco, categoria: cuentagotas
   - Proceso de windows enmascarado como un proceso sin firmar, categoria: evasion
   - El editor de ecuaciones de microsoft office genera un proceso del que se abusa con frecuencia, categoria: ejecucion
   - Archivo binario que se crea en un disco con una extension doble, categoria: ofuscacion de tipo de archivo
      
   - Proceso que intenta eliminar una herramienta de seguriad o antivirus conocida, categoria evasion
   - Powershell running with known mimikatz arguments, categoria coleccion
   - Proceso que se ejecuta desde la papelera de reciclaje, categoria evasion
   - Ejecutable creado en el disco por lsass.exe, categoria cuentagotas

3. Ejemplos de reglas BIOC en cortex XDR: IR a **Reglas > BIOC** para encontrar la pagina BIOC, esta pagina se enumeran todas las reglas BIOC integradas en el producto y que se pueden utilizar sin realizar cambios. puede editar o crear copias de estas firmas integradas mediante el generador de consultas y agregar sus propias exclusiones y ajustes
   
   Informacion sobre la consola de Cortex XDR
   - Name: nombre de BIOC
   - Tipo: Corresponde a la tactica o categoria MITRE ATT&CK a la que pertenece a la tecnica singular (Las de arriba, evasion, cuentagotas, etc)
   - Comportamiento: Es la firma que se creo
   - Severidad: Corresponde al riesgo de la tecnica. Si un ataque es de alta gravedad, es una tecnica de ataque es es muy arriesgada
   - Comentario: Descripcion de lo que es la tecnica del atacante

4. Caso practico: Busqueda de comportamientos de acceso a credenciales poco comunes mediante BIOC: En función de la metodología de desplazamiento a la derecha, debe centrarse en la búsqueda de la técnica de "volcado de memoria con comsvcs.dll", ya que es una técnica de acceso a credenciales. El acceso a credenciales como técnica es muy valioso para la búsqueda porque indica que un atacante puede haber progresado ya a través de los pasos para llegar a un punto de conexión y potencialmente ponerlo en peligro.
   
   - Comienzo: Busque comportamientos poco comunes de acceso a credenciales, como el acceso a credenciales sin usar herramientas como Mimikatz. Estas tecnicas son dificiles de detectar porque tienden a usar bibliotecas nativas del SO para volcar las credenciales de usuario
   - Formacion de casos de uso: Utilice BIOC incorporados, como el "volcado de memoria mediante comsvcs.dll" para buscar cualquier acierto
   - Recoleccion de herramientas: Utilice los cortex XDR BIOC como herramientas para esta busqueda.
   - Traduccion de casos de uso a firmas o analisis de datos: Segun el ciclo de vida de la busqueda de amenazas, traduzca los casos de uso a firmas en las herramientas.
   - Caza e investigacion: Por ultimo busca estas firmas especificas e investiga todo lo que encentres.

---
# CAZA ORIENTADA A LA FAMILIA DE MALWARE
1. Metodologia de "barrido": En la metodologia, la atencion se centra en familias especificas de malware, sus IOC asociados y las tacticas, tecnicas y procedimientos especificos de esa campaña de ataque o ese grupo de malware. El ataque generalmente comienza con una campaña de ataque general publicada en las noticias o en un blog de inteligencia de amenazas de codigo abierto.
   PAN tiene su propia unidad de inteligencia de amenazas: unit42 publica regularmente blogs sobre las ultimas campañas de los atacantes.
   
   Llevar a cabo una busqueda de amenazas para comportamientos especificos de la campaña:
   - Investigacion: Empieza por investigar el ataque (contexto del ataque, IOCs, tacticas especificas de los atacantes que se podrian buscar)
   - Identificar: Identifica todos los IOC y los indicadores que son exclusivos de esa campaña
   - Buscar: Busque puntos de conexion, su red y la nube. Tienen mecanismos de deteccion integrados de Cortex XDR que barren todo el entorno.

2. Caza del gorrion plateado: Silver Sparrow es una nueva cepa de malware que ataca a los sistemas MAC. La novedad de este malware proviene principalmente de la forma en que utiliza JavaScript para la ejecucion, la explotacion y la instalacion. El malware es particularmente interesante debido a su nueva variante y porque se dirige a los sistemas MAC. Infecto 29139 endpoints de macos.
   
   Como funciona silver sparrow: Para entender como funciona silver sparrow, usemos el ciclo de vida de progresion del atacante que vimos anteriormente y asignemoslo a como se comporta el silver sparrow
   - Explotacion: Esta familia de malware usa JS para su ejecucion y contiene dos paquete especificos malicosos
   - Instalacion: Una vez que el malware tiene los paquetes especificos, se instala mediante comandos JS maliciosos. usa una aplicacion llamada PListBuddy para iniciar un agente en las maquinas MAc de la victima. 
   - Comando y control: El malware se conecta a buckets maliciosos de AWS S3 para distribuir el contenido de la maquina victima y extraer mas instrucciones C2 ( Generalmente en forma de plantillas .json). Silver Sparrow "riza" especificamente estas instrucciones JSON de los dominios S3 maliciosos
   - Acciones sobre objetivos: Finalmente, el malware se encuentra la URL original desde la que se descargo el paquete y ejecuta una consulta SQLite3. Esta consulta indica al adversario que el malware se ha instalado y que sus canales de distribucion se han configurado correctamente.

3. Caso de estudio: Caza de malware para silver Sparrow: Este estudio de caso muestra la tecnica de busqueda orientada a la familia de malware para cazar silver Sparrow, un cluster de malware para MAC, usando XQL
   
   Ciclo de vida de caza para silver sparrow:
   - Comienzo: Comenzamos investigando los comportamientos y las IOC de silver sparrow
   - Formacion de casos de uso: Compruebe la posible actividad de C2 buscando todos los procesos de MAC que llaman a buckets de Amazon S3 y todos los IOC conocidos.
   - Recoleccion de herramientas: utilice las onsultas de Cortex XDR XQL y los IOC de cortex XDR como herramientas para esta consulta.
   - Traducccion de casos de uso a firmas o analisis de datos: Construir la consulta XQL de Cortex XDR yendo a investigacion > Generador de consultas > XQL. Los comportamientos especificos observados en este grupo de malware lo ayudaran a comprender que otros paquetes dentro de MAc se comportan de manera similar.
     
    En el generador de XQL construya la consulta que se muestra a continuacion para buscar el comportamiento C2 observado
    
   - Caza e investigacion: Realizar la investigacion en funcion de los resultados de la consulta.

4. Para mostrar los sistemas MacOS que muestran persistencia a través de las aplicaciones PListBuddy y LaunchAgents, ejecute la siguiente consulta:
_conjunto de datos = xdr_data_
_| filtro agent_os_type = AGENT_OS_MAC_
_| filtro actor_process_command_line = "*PlistBuddy*LaunchAgents*"_

Para mostrar los comportamientos de MacOS que ejecutan una consulta SQLite3 para indicar que la instalación se ha realizado correctamente en el servidor C2, ejecute la siguiente consulta:
_conjunto de datos = xdr_data_
_| filtro agent_os_type = AGENT_OS_MAC_
_| filtro actor_process_command_line = "*LSQuarantine*"_



---
# BUSQUEDA ORIENTADA A DATOS - data oriented hunting
1. Caso practico: Busqueda de comportamientos de procesos, servicios y ejecuciones automaticas poco comunes mediante la biblioteca de consutlas XQL:  En esta modalidad de caza, no hay una hipotesis especifica. En su lugar, se comienza con consultas integradas que buscan anomalias y van directamente a la busqueda e investigacion de parte del ciclo de vida de la busqueda de amenazas. Puede aprovechar cortex XDR, XQL library y host insights para realizar esta busqueda.
   
   Caza e investigacion: **Investigacion > Generador de consultas > XQL** y acceda a la biblioteca de consultas. La biblioteca de consultas viene lista para usar con cortex XDR.
