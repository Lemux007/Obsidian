#Nodo
METODOLOGIAS Y RECURSOS DE SOLUCION DE PROBLEMAS
1. Actividades de solucion de problemas: Disciplina de ingenieria que consta de habilidades en estas areas: 
	1. Metodologias
	2. Base de conocimientos, documentacion y recursos (Sitios web utiles)
	3. Solucion de problemas de herramientas y utilidades: principal Cytool
	4. Registros y rastreos
	5. Trabajar con el equipo de soporte
2. Enfoque DIReC
	- Definir, el problema en terminos especificos
	- Yo (I), Aislar con herramientas y tecnicas la causa raiz de un problema
	- Resolver el problema
	- Confirmar la eficacia y la permanencia de la resolucion.
3. Flujo general de solucion de problemas
	- Verificar el problema
	- Recopilacion de datos
	- Extraer hipotesis
	- Reducir hipotesis
	- Encuentre la causa raiz

4. Caza de amenazas gestionadas de Cortex XDR
	Cortex XDR Managed Threat Hunting (MTH), es el primer servicio de busqueda de amenazas de la industria que aprovecha datos recopilados para encontrar amenazas sofisticadas, ocultas o inadvertidas utilizando la experiencia de nuestros cazadores de amenazas y herramientas y metodologias de busqueda.
	Capacidades de XDR Managed Threat hunting:
	- Experiencia de la unidad 42: Los cazadores de amenazas monitorean continuamente el entorno.
	- Basado en Cortex XDR: Encuentre todos los ataques con detecciones de alta fidelidad basadas en la visibilidad holistica
	- Enriquecido por un contexto omnipresente

5. Unidad 42: Capacidad de respuesta mundial
	Grupo de elite de investigadores ciberneticos y respondedores de incidentes, brindan servicios globales de respuesta a incidentes y gestion de riesgos ciberneticos.
	- Respuesta a la violacion de datos: identificar, contener y erradicar amenazas.
	- Gestion del riesgo cibernetico y la resiliencia: detecta y evalua de forma proactiva ciberamenazas para madurar el programa de seguridad
	- Investigaciones digitales: Recopilan, recuperan e interpretan la informacion obtenida.
	- Analisis de datos e inteligencia: Encuentra informacion confidencial en riesgo en una violacion de datos de forma rapida fiable y a coste menor
	- Perito y apoyo en litigios: Trabaja con equipos legales para revisar la evidencia y proporcionar informacion de testigos expertos en informes, declaraciones y testimonios.

ALMACENES DE DATOS DE AGENTES
1. Aplicacion Cortex XDR Cytool
   La aplicacion cytool es la interfaz de linea de comandos para administradores cuando trabajan con el agente XDR.
   - Consultar y gestionar funciones basicas y avanzadas en el endpoint

2. Ubicaciones de datos de configuracion del agente
	1. Archivos binarios y BD para la configuracion: **%PROGRAMDATA%\Cyvera\LocalSystem** contiene archivos binarios y bases de datos para la configuración
	2. Configuracion relacionada con el agente: **HKLM\SYSTEM\Cyvera**.

3. BD persistentes de agentes: Los componentes del agente usan datos clave-valor en disco para la persistencia de sus datos privados, que se almacenan en archivos **%PROGRAMDATA%\Cyvera\LocalSystem\Persistence**.
   Lista parcial de BD LocalSystem/Persistence
	![[Pasted image 20241205160548.png]] ![[Pasted image 20241205160557.png]] 
	Crear archivos JSON comando: cytool persist export
	![[Pasted image 20241205160723.png]] 
	Mostrar configuraciones de comunicacion importantes (Direcciones de red en la nube): cytool persist print cloid_frontend.db


IDENTIFICACION DEL AGENTE
1. Identificadores de agentes unicos: XDR utiliza dos ID, conocidos como ID de end point e ID de maquina, para identificar de forma unica el SW y el HW de XDR respectivamente.
   Los identificadores se almacenan en agent.id y hardware.id en la carpeta **%PROGRAMDATA%\Cyvera\LocalSystem\OsPersistence**.

REGISTRO DE AGENTES DE CORTEX XDR
	Los componentes del agente de Cortex XDR escriben en trapsd.og para registrar sus acciones, como cambios de servicio y estado, actualizaciones de políticas y creación de alertas

- Archivo de texto con formato de registro: Abrir archivo de registro en la consola XDR o desde **%PROGRAMDATA%\Cyvera\Logs\trapsd.log** 
![[Pasted image 20241205161737.png]]

- Configuracion del nivel de registro: Se puede usar Cytool para cambiar los niveles de registro de los componentes del agente XDR.
![[Pasted image 20241205161846.png]]


TRABAJAR CON EL SOPORTE TECNICO 
1. Archivo de soporte (Support File): Es un archivo comprimido y archivado que agrega todos los registros de un punto de conexion. Generado bajo demanda para ayudar al soporte tecnico de PAN a solucionar y diagnosticar problemas del sistema.
	- Recuperar o generar Support File methods: Iniciar la recuperacion de un archivo de soporte desde un endpoint mediante la accion Enpoint Control > Recuperar archivo de soporte
	- Generación de archivos de soporte desde la consola del agente: Si el endpoint esta desconectado de la consola de gestion de Cortex XDR, dispone de otras opciones para generar un archivo de soporte directamente desde el endpoint.
	  
	  Click en **Generar archivo de soporte** En la consola del agente.O buscar el archivo **%APPDATA%\PaloAltoNetworks\Traps\support\logs_GUID** 
	- Generacion de archivos de soporte a traves de Cytool: Usando comando **Cytool log collect** o Generar archivo de soporte **%APPDATA%\PaloAltoNetworks\Traps\support**

2. Tokens de agente: Cortex XDR ahora admite la capacidad de crear, recuperar y usar tokens de agente.
   - Util cuando un administrador no necesita conocer la contraseña del agente, pero aun necesita acceder y realizar operaciones del agente.

3. Creación de un caso de soporte técnico: Inicio > lista de casos y click en obtener ayuda. Anexar toda la info.
