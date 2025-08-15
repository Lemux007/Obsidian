INVENTARIO DE ACTIVOS
1. Activo de red / Network Assets: Es cualquiero nodo direccionable IP en una red informatica. Por ejemplo un equipo host o un enrutador. Ej: Un equipo host o un router. 
   Es como minimo, un dispositivo compatible con IP en su red. 
   - Activos administrados: Son activos de red la cual tiene agente Cortex XDR instalado
   - Activos no administrados: Activos de red que no tienen el agente Cortex XDR.
     
2. Inventario de activos: **Asset Inventory > All assets** proporciona una tabla unificada de todos los activos de su red que pueden administrar o no. **Specific Assets** muestra los actios en dos listas independientes por tipo. 
   Atributos clave: Puede encontrar los atributos clave de los activos de red en la tabla Todos los activos. 
   - Tipo: Tipo de recurso
   - Tiene agente XDR: Si o no
   - Fuentes: Los origenes son los nombres de los componentes que detectaron el recurso.: nube, XDR, ASM, syslog, SSO, Azure AD, NGFW, escaner de agente.
   - Rangos de IP internos: Rango de direcciones a los que pertenece este recurso.
   - Primera y ultima observacion: MArcas de tiempo de cuando se vio el recurso por primera vez y por ultima vez.

3. Trabajar con activos de red: Click en algun recurso para abrir el panel lateral y ver mas detalles orgnizados en secciones.  Acciones:
   - Vista IP abierta: IP View muestra los datos de red relacionados con las direcciones IP de este recursos como: protocolos de red, puertos, volumen de trafico por conexiones entrantes y salientes.
   - Abrir en Quick Launcher: Muestra un resumen de la sacciones de investigacion y respuesta relacionadas con las direcciones IP de este recurso.


CONFIGURACION DE RED
1. Deteccion de activos de red: Cortex XDR combina la configuracion de red definida por el usuario con los resultados de deteccion automatica del analisis de los registros de red recompilados. Hay dos conjuntos complementarios de tareas para la deteccion de redes.
   1. Configuracion de red manuales ( definidas por el usuario): Desde la consola de administracion de configuracion de red, defina los rangos de direcciones ip y los nombres de dominio para la red interna
   2. Descubrimiento automatizado de nodos: XDR extrae automaticamente las direcciones IP y sus redes IP de registros especificos, entre los que se incluyen: 
	   1. Registros de agentes de cortex XDR
	   2. Cache ARP
	   3. Mapeador de red de VM de broker
	   4. Recopilador DHCP de windows
	   5. Colector de datos Pathfinder
	   6. Datos EDR recopilados de los registros de firewall

2. Rangos de direcciones IP: permite definir los rangos de direcciones IP en su red interna. LA tabla de rangos de direcciones ip incluye automaticamente los rangos de ipv4 privadas conocidas y el rango de direccionamiento automatico de ip privadas (APIPA).
   - Active Assets: Numerot de todos los activos detectados en este rango ip
   - Active managed assets: Numero de todos los activos administrados detectados en este intervalo de IP
    
	Crear un nuevo rango de direcciones IP:
	- Ir a **Configuracion de red > Rangos de direcciones IP** y seleccionar **Agregar nuevo rango** y clic en **crear nuevo**
	- iNTRODUCIR EL NOMBRE DE INTERVALO Y UN INTERVALO DE DIRECCIONES IPV4 O cidr, COMO SE INDICA A CONTINUACION:
		  - Rango de direcciones IP: EJ: 192.18.2.0 - 192.168.2.255
		  - CIDR EJ: 192.168.2.0/24

3. Configuracion del asignador de red de VM del Broker: En esta seccion se muesra como afectan los rangos de direcciones ip definidos por el usuario a la configuracion del asignador de red de VM de intermediario
	1. Configuracion: Primero se debe definir los rangos de direccion ip y a continuacion, seleccionar uno o mas de los rangos definidos durante la configuracion del mapeador de red.
	2. Ejecucion: El asignador de red analiza la red para detectar host no administrados por intervalo de direcciones ip seleccionado.

4. Evaluacion de vulnerabilidades: 
	1. La evaluacion de vulnerabilidades es un componente del complemento Host Insights. Dicho componente encuentra vulnerabilidades y exposiciones comunes (CVE) que pueden existir en las aplicaciones instaladas y los kernels del SO. La limitacion es que solo analiza el kerlen del SO, no las aplicaciones de windows.
	   
	   Como funcionan la evaluacion de vulnerabilidades:
	   - Actualizacion de la BD de CVE
	   - Busqueda periodica de CVE DB: Se busca periodicamente en la base de datos de CVE los numeros de version de las aplicaciones y kernels del SO.
	   - Reporte de impacto potencial

	  Acceder a la pagina de evaluacion de vulnerabilidades: **Menu superior de activos > Activos > Evaluacion de vulnerabilidades > Evaluacion de vulnerabilidades**
	  
	  Configurar la evaluacion de vulnerabilidades: Requiere la licencia del complemento Cortex XDR HOST insights, una vez obtenida habilitar la recopilacion de datos de inventario de host para agentes XDR

