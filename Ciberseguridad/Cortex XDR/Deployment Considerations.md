# PORTAL DE ATENCION AL CLIENTE
1. Identidades de CSP: Existen dos identidades:
   - Cuenta CSP: Una cuenta de CSP identifica una empresa, una organización o un equipo. También se puede conocer como una cuenta de soporte técnico, una cuenta de empresa (u organización) de CSP o simplemente una cuenta en el contexto de CSP.
   - Usuario de CSP: Un usuario de CSP identifica a una persona. Aunque no puede crear una nueva cuenta de CSP como usuario de CSP de inicio de sesión, puede crear nuevos usuarios de CSP y agregarlos a sus cuentas de CSP autorizadas como miembros.

2. Administrar usuarios de CSP: La pagina Administrar usuarios ayuda a crear y administrar usuarios de CSP en la cuenta actual
   - La página **Miembro** > **administrar** **usuarios** muestra los usuarios autorizados de CSP en la cuenta de CSP actual, que se muestra en la parte superior de la página.
   - Introduzca la dirección de correo electrónico del usuario, ya que es la clave para localizar al usuario. Debe crear el usuario antes de poder agregarlo a la cuenta. Ingrese las fechas de activación y vencimiento de la membresía. La fecha de activación puede ser cualquier fecha en el futuro.

1. Usuario incial de CSP y cuenta de CSP: Estas se crean automáticamente cuando compra un producto de PAN por primera vez. Al primer usuario CSP se le asigna el rol de superusuario de CSP para la cuenta y se le da el rol administrador de cuentas XDR.

# SERVICIOS DE INFRAESTRUCTURA DE CORTEX
1. Requisitos de la instancia de Cortex XDR: Una instancia de XDR requiere servicios de infraestructura que deben estar enlazados a regiones especificas. 
   Instancias basadas en la nube:
   - Wildfire: Inteligencia de amenazas en forma de analisis
   - Lago de datos de Cortex: Cortex data lake es un servicio opcional que proporciona almacenamiento basado en la nube para registros a largo plazo
   - Motor de identidad en la nube (CIE): Servicio opcional que proporciona informacion de identidad a cortex XDR extrayendo la informacion del directorio de las organizaciones.
     
    Regiones de instalacion de Cortex XDR:
    - America del norte (Canada, EU)
    - Europa (UE, CH, UK)
    - Asia (JP, SG)

2. Gestion de los servicios de infraestructura de Cortex: Se puede administrar servicios de infraestructura con herramientas: 
   - ## Centro de redes de Palo Alto: 
    El concentrador de Palo Alto Networks es la interfaz de usuario de los servicios de infraestructura de Cortex, donde puede administrar las instancias de servicio. La administración incluye tareas como la creación de nuevas instancias de servicio, la asignación de roles a los usuarios de CSP por instancia y el acceso a las instancias.
    
    - ## Lago de datos de Cortex
    Cortex Data Lake es un servicio de almacenamiento de datos basado en la nube que se utiliza para recopilar y almacenar datos y registros de varias fuentes de datos. Los tipos de datos almacenados en una instancia de Cortex Data Lake incluyen:
    1. Registros de red generados por firewalls como NGFW
    2. Registros en la nube generados por aplicaciones de seguridad de la nube
    3. Alertas externas enviadas por la API de XDR y el recopilador de syslog

3. Motor de identidad en la nube: CIE, anteriormente conocido como servicio de sincronización de directorios, es un servicio en la nube para el acceso de solo lectura a la información de directorio local de las organizaciones. El directorio puede ser Azure Active Directory (AD). El servicio es utilizado por una instancia de Cortex XDR para acceder a los datos de identidad.
   Una implementacion de CIE consta de dos componentes: 1. Una instancia CIe basada en la nube y agentes de windows locales conectados a controladores de dominio.


# ACTIVACION DE INSTANCIAS DE CORTEX XDR
1. La activación de Cortex XDR crea una nueva instancia de Cortex XDR, también conocida como inquilino. La activación es una tarea única que finaliza con el aprovisionamiento de bases de datos y servicios de middleware basados en la nube. El superusuario recibe un correo electrónico de activación que contiene un enlace a Cortex Gateway. Para poder activar una instancia de Cortex XDR en una cuenta de CSP, se le debe asignar un rol de administrador de cuenta de XDR obligatorio.
   
   Para activar una instancia ir a **Tenant navigator > Cortex > gateway > Disponible para la activacion**, buscar el numero de serie y click en activar  el gateway esta en https://xdr-gateway.paloaltonetworks.com/

2. Configuracion de la instancia: Atributos para un inquilino mediante cortex Gateway:
   - Nombre del inquilino, descriptivo para la instancia
   - Region: Donde se dessea instalar la instancia de XDRy todos los servicios de infraestructura dependientes incluida Cortex Data Lake
   - Subdominio de inquilino: Nombre de un subdominio unico en la region. valido en la especificacion de dominio completo (FQDN)
     
     Las especificaciones de la región y el subdominio del inquilino forman una dirección HTTPS única para la instancia de Cortex XDR, a la que puede acceder en https://subdominio.xdr.region.paloaltonetworks.com.

3. Verificacion de instancias: **Cortex Gateway > Inquilino disponible** y estatus activo


# CONTROL DE ACCESO
1. Gestion de roles de Cortex XDR: Puede administrar las funciones XDR a traves de cortex gateway (Vinculadas a la cuenta de CSP) o la consola de administracion de xdr (Solo para la instancia XDR actual), ambos proporcionan paginas y aacciones para administrar roles y permisos XDR.
   
   XDR Roles: ![[Pasted image 20241210142256.png]]

2. Pagina de roles: Nuevos roles
   ***Configuracion > Configuraciones > Administracion de acceso > Funciones > +Nueva funcion > "Nombre de rol" > Permisos: Vista y acciones > Guardar***

3. Control de acceso basado en alcance (SBAC): Con SBAC, puede restringir el acceso de los usuarios a las áreas funcionales de la consola de administración por ámbito.
   Restricciones a usuarios: 
   - Administracion de endpoints
   - Centro de actividades
   - Cuadros de mando e informes
   - Incidencias y alertas

	Configuracion SBAC: ***Configuracion > Configuraciones > Administracion de acceso > Usuarios***

