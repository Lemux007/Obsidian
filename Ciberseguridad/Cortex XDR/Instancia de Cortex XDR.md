#subnodo

1. Capacidades de la instancia de Cortex XDR:
	1. Gestion de puntos finales: Proporciona capacidades centralizadas para administrar agentes de corte XDR en los terminales, como agrupar los terminales en funcion a algunos criterios, crear paquetes de instalacion, o actualizar software de forma masiva.
	2. Administracion de la configuracion de seguridad de endpoints: Despues de instalar, administramos la config de seguridad de los endpoints mediante la creacion de perfiles o deshabilitar caracteristicas de proteccion, llamados modulos de proteccion.
	3. Investigacion
	4. Acciones de respuesta: La instancia puede responder a ataques
	5. Capacidades de deteccion avanzadas: recopilacion de registros, ingesta y la correlacion
	6. Capacidades de busqueda
	7. Caracteristicas complementarias
	8. Integracion
	9. Panel de control e informes

2. Log stitching / costura de troncos: A continuación, Cortex XDR correlaciona y une los registros de varios sensores para revelar las causalidades de las amenazas y los plazos que simplifican la investigación de las amenazas y le permiten identificar la causa raíz de las actividades sospechosas notificadas como alertas. Una alerta puede informar de un único proceso de ataque en un único punto de conexión.
	1. Alertas y datos de registro de endpoints mejorados: Visibilidad completa sobre el trafico de red, comportamiento del usuario y la actividad de los endpoints
	2. Artefactos y activos: Artefactos: componentes implicados en el ataque, como procesos maliciosos, direcciones ip y archivos (hashes), Activo: Componentes afectados o victimas de los ataques, como endpoints y usuarios.

3. Analisis de causalidad ilustrado: Los procesos involucrados en un ataque se muestran en un grafico de instancia de causalidad que muestra los diversos procesos involucrados en un ataque basado en scripts.

4. Deteccion de actividad anormal: A lo largo de todo su ciclo de vida, un sistema de seguridad de red defensiva debe estar correctamente configurado y actualizado el 100 por ciento del tiempo para evitar atacantes decididos. Los sistemas de red pueden verse comprometidos, a menos que estén completamente automatizados y construidos mediante aprendizaje automático (ML) para estar preparados de forma proactiva para el próximo ataque avanzado.
   
   Motor de analisis Cortex XDR: Contiene un motor de analisis que detecta automaticamente el comportamiento anormal del usuario y las actividades de los endpoints y de la red. usa ML supervisado y no supervisado.

5. Recogida de datos: XDR puede recopilar y categorizar registros y datos de alertas de una variedad de fuentes externas. 
   Metodos de investigacion: 
   - Red: Registros de conexion recopilados de productos y servicios de red (Checkpoint, FW1 VPN1, Cisco asa, DHCP)
   - Autenticacion: Registros recopilados de los servicios de autenticacion (Azure AD, Okta, pingfederate)
   - Extremo: Registros como el recopilador de eventos de windows
   - Proveedor de nube publica: Registros de operaciones y sistemas de proveedores de nube (Kubernetes, GCP, prisma cloud)
   - Registros externos personalizados: Cualquier registro de proveedor almacenado o enviado a traves de syslog en CEF, LEEF, FTP, CSV, HTTP o almacenado en una BD de datos relacional.
 
6. Compatibilidad con XQL: XQL permite consultar datos sin procesar ingeridos en corte XDR para el analisis de eventos de red y endpoints. usado para correlacionar manualmente registros y alertas

7. Acciones de respuesta: Para responder a los ataques, puede iniciar acciones de respuesta inmediata manualmente desde la consola de admin de XDR. La mayoria de las acciones que se inician desde la consola de admin se transfieren inmediatamente a los agentes a traves de canales de comunicacion en vivo, websocket, no HTTP.

8. Integraciones:  Puede configurar una integracion de salida para enviar alertas e informes a la plataforma que elija
   - Servicios de inteligencia de amenazas: Fuentes de veredictos como Wildfire, autofocus y virustotal. 
   - gestion de incidentes externos: Podemos integrar Cortex XDR con cortex XSOAR para enviar alertas a XSOAR para dar una respuesta automatizada y coordinada a las amenazas. 
   - Claves de API
   - Motor de identidad en la nube: Cloud identify engine es un servicio que proporciona informacion de dominio de Active Directory local de las organizaciones para aplicaciones que incluyen XDR
