#Nodo

1. Requisitos de la instancia de Cortex XDR: Una instancia de XDR requiere servicios de infraestructura que deben estar enlazados a regiones especificas. 
   Instancias basadas en la nube:
   - Wildfire: Inteligencia de amenazas en forma de analisis
   - Lago de datos de Cortex: Cortex data lake es un servicio opcional que proporciona almacenamiento basado en la nube para registros a largo plazo
   - Motor de identidad en la nube (CIE): Servicio opcional que proporciona informacion de identidad a cortex XDR extrayendo la informacion del directorio de las organizaciones.
     
    Regiones de instalacion de Cortex XDR:
    - America del norte (Canada, EU)
    - Europa (UE, CH, UK)
    - Asia (JP, SG)

1. . Gestion de los servicios de infraestructura de Cortex: Se puede administrar servicios de infraestructura con herramientas: 
   - ## Centro de redes de Palo Alto: 
    El concentrador de Palo Alto Networks es la interfaz de usuario de los servicios de infraestructura de Cortex, donde puede administrar las instancias de servicio. La administración incluye tareas como la creación de nuevas instancias de servicio, la asignación de roles a los usuarios de CSP por instancia y el acceso a las instancias.
    
    - ## Lago de datos de Cortex
    Cortex Data Lake es un servicio de almacenamiento de datos basado en la nube que se utiliza para recopilar y almacenar datos y registros de varias fuentes de datos. Los tipos de datos almacenados en una instancia de Cortex Data Lake incluyen:
    1. Registros de red generados por firewalls como NGFW
    2. Registros en la nube generados por aplicaciones de seguridad de la nube
    3. Alertas externas enviadas por la API de XDR y el recopilador de syslog

3. Motor de identidad en la nube: CIE, anteriormente conocido como servicio de sincronización de directorios, es un servicio en la nube para el acceso de solo lectura a la información de directorio local de las organizaciones. El directorio puede ser Azure Active Directory (AD). El servicio es utilizado por una instancia de Cortex XDR para acceder a los datos de identidad.
   Una implementacion de CIE consta de dos componentes: 1. Una instancia CIe basada en la nube y agentes de windows locales conectados a controladores de dominio.