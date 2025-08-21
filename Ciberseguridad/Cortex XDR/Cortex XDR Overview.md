#Nodo
# AGENTE DE CORTEX XDR
1. Componentes principales de Cortex XDR: Consta de una instancia de XDR basada en la nube y agentes de cortex XDR instalados en los puntos finales de las organizaciones en las instalaciones o en la nube. 
   - **Instancia de Cortex XDR**: Una instancia de Cortex XDR es un componente en la nube que proporciona una gestión centralizada de la seguridad de los endpoints de las organizaciones, incluida la gestión de endpoints, la gestión de políticas de seguridad en los endpoints, la investigación de incidentes y alertas, y la respuesta a las amenazas.
   - **Agente de Cortex XDR**: El agente de Cortex XDR es el componente local de Cortex XDR. El componente del agente proporciona protección contra exploits y malware multimétodo para endpoints.

2. Capacidades basicas del agente Cortex XDR: Capacidades para mejorar la seguridad y evitar malware y exploits:
   - Prevencion de malware y exploits: El malware desconocido se detecta a través de motores locales basados en aprendizaje automático en los endpoints; Los motores inspeccionan los archivos utilizando técnicas de análisis estático y también los procesos utilizando técnicas de análisis de comportamiento basadas en reglas.
   - Seguridad extendida de endpoints: El agente proporciona extensiones para reforzar la seguridad minimizando la superficie de ataque en los puntos de conexión. Por ejemplo, la función de control de dispositivos de Cortex XDR le permite desactivar por completo los dispositivos conectados a bus serie universal (USB) a través de políticas personalizables.
   - Escaneo de puntos finales: El agente de Cortex puede analizar los endpoints en busca de malware inactivo que no esté intentando ejecutarse activamente. El agente examina los archivos en el endpoint de acuerdo con el perfil de seguridad de malware que está en vigor en el endpoint.
   - Carga de datos: Después de proteger localmente su endpoint de los ataques, un agente de Cortex XDR envía inmediatamente la alerta de prevención a una instancia de Cortex XDR para su posterior análisis centralizado. El agente también puede recopilar y cargar periódicamente datos de punto de conexión mejorados en la instancia de Cortex XDR, donde la instancia puede correlacionar todos los conjuntos de datos entrantes para detectar amenazas persistentes avanzadas en sus primeras etapas.
   - Busqueda y destruccion de archivos: El agente crea y mantiene una BD que incluye hashes de archivos y rutas para poder localizar y destruir rapidamente cuaquier archivo malicioso.

3. Ciclo de vida de los ciberataques: Un atacante debe seguir una secuencia de eventos para infiltrarse con exito en una red y extraer datos de ella. 
   - Reconocimiento: Investigan, identifican y seleccionan objetivos
   - Militarizacion: Se determina que metodos utilizar, incrustar codigo en pdfs archivos word, etc.
   - Entrega: Se tratara de entregar el codigo del intruso a la organizacion. Usb dejadas, correo electronico, phishing.
   - Explotacion: Una vez obtenido acceso en una organizacion pueden activar el codigo de ataque
   - Instalacion: Se tratara de establecer operaciones con privilegios, instalar root kit, escalar priviilegios o establecer persistencia
   - Comando y control: Se establece un canal de comando a traves de internet a un servidor especifico.
   - Actuar en funcion del objetivo: Podrian querer filtrar datos, destruir infraestructuras criticas, desfigurar la propiedad web, crear miedo o extorsionar.

4. Comprender las amenazas: exploits, Independientemente de su propósito, todos los ataques deben comenzar con un compromiso inicial de un sistema de punto final. Hoy en día, los ataques combinan dos métodos para lograr este objetivo inicial: explotar un endpoint vulnerable y luego ejecutar malware.
5. Comprender las amenazas: malware, Mientras que un exploit viene en un archivo de datos que contiene código incrustado maliciosamente, el malware viene como un archivo o script directamente ejecutable con intenciones maliciosas. Estos a menudo requieren un componente de engaño para hacer que el usuario final inicie el archivo. 
   Posibles signos de malware: - Archivo creado recientemente - Ejecutable sin firmar - Archivo que intenta ejecutarse desde una carpeta sospechosa (temporal) - Archivo que muestra comportamiento sospepchoso, como intentar crear un proceso secundario para realizar una accion inesperada.

6. Flujo de prevencion de exploits: Cuando un usuario intenta abrir un archivo armado, como un PDF, se desarrolla un proceso.
   ![[Pasted image 20241211100757.png]]
   - Cuando un usuario intenta abrir un documento, el sistema operativo encuentra una aplicación asociada y crea un nuevo proceso a partir de los archivos ejecutables de la aplicación.
   - En este punto, el agente Cortex XDR inyecta sin problemas sus módulos de protección contra exploits (EPM) en forma de bibliotecas de enlaces dinámicos (DLL) en el proceso que se está creando.
   - Una vez finalizada por completo la creación del proceso, se inicia un subproceso del agente Cortex XDR, junto con subprocesos de otras aplicaciones.
   - Una vez que el agente de Cortex XDR ha inyectado los EPM en el proceso, protege el proceso de los exploits.
   - Si se realiza un intento de exploit, el subproceso de protección del agente de Cortex XDR bloqueará inmediatamente la técnica o técnicas, finalizará el proceso y notificará tanto al usuario como al administrador que se ha frustrado un ataque.

7. Proteccion contra malware: Consiste en un analisis previo a la ejecucion y un seguimiento posterior a la ejecucion.
	1. Analisis previo a la ejecucion: En el examen secuencial de archivos, los modulos de proteccion previa a la ejecucion se utilizan para obtener una decision antes de que se permite la ejecucion de un archivo. un bloqueo o permitir una desicion tiene el siguiente flujo:
	   - Modulos de proteccion de malware especificamente diseñados para un tipo de ataque. 
	   - Las restricciones son simples listas de direcciones y caminos desde donde los usuarios puedan correr archivos
	   - Veredicto de hash de wildfire y el local analysis
	     ![[Pasted image 20241211101931.png|800]]
	 1. Monitoreo posterior a la ejecucion: Una vez que los modulos de protección finalizan el examen permiten ejecutar el archivo y los modulos de proteccion posteriores a la ejecucion comienzan a monitorear continuamente las actividades del proceso en curso para detectar cualquier comportamiento anormal.
	    ![[Pasted image 20241211102126.png]]
8. Carga de alertas y registros: XDR puede cargar dos tipos de datos: Alertas y Registros
   - Alertas: Las alertas se crean inmediatamente para capturar los detalles de las actividades sospechosas y se cargan inmediatamente en Cortex XDR. Las alertas pueden contener información como un nombre, una ruta de acceso, un ID de proceso del proceso malintencionado, la fecha y la hora del ataque y el nombre del módulo de prevención.
   - Registros: Los registros se cargan periódicamente (normalmente cada 5 minutos) y pueden contener información sobre eventos del sistema operativo. Los registros no contienen necesariamente información relacionada con los ataques.
	 ![[Pasted image 20241211102413.png]]

9. Refuerzo de la seguridad de los endpoints: XDR proporciona extensiones para ampliar la seguridad de sus terminales mas alla de las capacidades de prevencion integradas del agente XDR
   Tipos de extensiones Cortex XDR (Refuerzan la seguridad, centralizados, gestion en consola, aplicados localmente): 
   - Control de dispositivos: Bloquea o permite dispositivos USB dentro de su organización. Los dispositivos incluyen unidades de memoria de solo lectura (CD-ROM) de disco compacto, unidades de disco duro (HD) y USB extraíbles.
   - Host firewall: Bloquea o permite el trafico entrante y saliente en los puntos de conexion a traves de las reglas compuestas por caracteristicas de comunicacion, incluida la direccion ip o los rangos de direcciones ip.
   - Cifrado de disco de host: Podemos aplicar cifrado o descifrado bitlocker en los endpoints

[[Instancia de Cortex XDR]]
[[Ofertas de productos y licencias]]
