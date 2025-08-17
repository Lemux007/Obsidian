# Cortex XDR Ingestion flow / Flujo de ingesta de Cortex XDR
1. Componentes del flujo de ingesta: El flujo de ingesta de Cortex XDR consta de Cortex XDR, un componente en la nube, y tres componentes locales, entre los que se incluyen Broker VM Syslog Collector, Broker VM y XDR Collectors.
   ![[Pasted image 20241210165247.png]]
- Recopilación de registros desde la nube: Los proveedores de nube pública, como AWS, Azure y GCP, pueden enviar varios tipos de registros a Cortex XDR. Los registros del proveedor de nube incluyen los tipos de red, flujo y auditoría. Para recopilar registros de la nube, es necesario configurar tanto la nube proporcionada como la consola de administración de Cortex XDR
- Recopiladores locales: En las instalaciones, las máquinas virtuales de Broker y los recopiladores de XDR pueden recopilar varios tipos de registros, incluidos los registros de eventos de punto final. Estos componentes también pueden funcionar como motores de reglas de análisis. Se pueden adjuntar varias instancias de VM de Broker e instancias de XDR Collector a la misma instancia de XDR. Además, la máquina virtual de Broker proporciona varios componentes dedicados (también conocidos como applets) para recopilar registros de esas aplicaciones conocidas, como bases de datos relacionales, servidores FTP, servidores HTTP y cualquier registro con formato CVS en las carpetas compartidas.

2. Reglas de analisis: Las reglas de análisis de Cortex XDR forman parte del flujo de ingesta de datos de Cortex XDR. Un motor de reglas de análisis analiza una entrada de registro sin procesar, aplica la lógica de regla a los campos de registro de entrada de análisis y, a continuación, prepara y devuelve una o varias filas para agregarlas a los conjuntos de datos. Las reglas de análisis se compilan en la instancia de Cortex XDR y, a continuación, se pasan a las instancias de Broker VM y XDR Collector conectadas.
   - Proposito de las reglas de analisis: Eliminar datos irrelevantes de los registros sin procesar entrantes. Beneficio neto de organizar y limpiar los registros antes de almacenarlos es doble:
     - Reduccion de datos ahorra espacio de almacenamiento
     - Conjuntos de datos minimizados y organizados de forma eficaz mejoran el rendimiento de las consultas XQL.
 - Autorizacion para analizar reglas: Un usuario debe ter+ner privilegios de administrador de cuentas y administrador de instancias de cortex XDR


# GESTION DE CONJUNTO DE DATOS
1. Conjunto de datos XDR de cortex: un conjunto de datos es un almacenamiento persistente para contener pares atributo-valor. Cortex XDR almacena registros en conjuntos de datos y los motores de búsqueda XDR (como XQL y Query Builder) ejecutan consultas en uno o más conjuntos de datos. Los conjuntos de datos XDR están sujetos a políticas de retención de datos.
2. Gestión de conjuntos de datos: **Configuracion > Administracion de datos > administracion de conjuntos de datos**
   - Nombre del conjunto de datos
   - Destino de consulta predeterminado: Esta columna indica si el conjunto de datos es el conjunto de datos predeterminado. De forma predeterminada, solo el conjunto de datos xdr_data se configura como Destino de consulta predeterminado y este campo se establece en **Sí**
   - Tipo: Tipo de conjunto de datos (System, raw, user, system audit)
   - Rango caliente y rango frio: Estas dos columnas muestran el período exacto del almacenamiento en caliente y el almacenamiento en frío desde la fecha de inicio hasta la fecha de finalización, respectivamente.
3. Tipo de conjuntos de datos: Puede administrar y configurar el control de acceso granular a conjuntos de datos desde **Configuraciones > Administración de acceso > Roles**. Una vez que habilite la opción Habilitar la administración de acceso al conjunto de datos, debe definir los permisos de acceso que desea conceder para el rol para cada tipo de conjunto de datos. Tenga en cuenta que las opciones difieren según el tipo de conjunto de datos.
   - Sistema: Cortex XDR crea conjuntos de datos del sistema incluidos email_data, xdr_data. xdr_dhcp, host_inventory
   - Crudo_ Conjunto de datos sin procesar son panw_network_mapper_raw y unknown_unknown_raw. 
     El conjunto de datos panw_network_mapper_raw es generado por la aplicación Broker VM Network Mapper, 
     mientras que el conjunto de datos unknown_unknown_raw es para almacenar registros no resueltos con atributos de producto y proveedor.
   - Usuario: Conjunto de datos de usuario se crean mediante consultas XQL
   - Correlacion: Se crean mediante las reglas de correlacion XDR

4. Retencion de datos: **Administracion de datos > administracion de conjunto de datos** muestra la duracion de la retencion de la instancia de XDR en la parte superior de la pagina. 30 dias para todos los tipos de datos ingeridos y 180 dias para los datos de alertas e incidentes.
   - Almacenamiento en caliente: Almacenamiento con capacidad de busqueda completa. se usaba antes del almacenamiento en frio
   - Almacenamiento en frio: Mas barato y a menudo se usa para necsidades de cumplimiento a largo plazo, capacidades de busqueda limitada.

5. Acciones del conjunto de datos: **Click derecho en un conjunto de datos de la tabla de conjunto de datos > Ver esquema, establecer como predeterminado, eliminar y descargar**
   ![[Pasted image 20241210171442.png]]
6. Conjunto de datos de busqueda: Puede cargar archivos con valores separados por comas (CSV), valores separados por tabulaciones (TSV) o con formato JSON en cortex XDR como conjunto de datos de busqueda.
7. Control de acceso basado en roles para conjunto de datos: De forma predeterminada, el control de acceso basado en roles (RBAC) en conjuntos de datos no está habilitado; Todos los usuarios de la consola de administración tienen acceso a todos los conjuntos de datos. Puede habilitar y definir permisos de acceso para un rol personalizado en un conjunto de datos o por tipo de conjunto de datos a través **de Configuraciones > Administración de acceso > Roles**. Para configurar los controles de acceso primero debera crear un nuevo rol.


ALERTAS EXTERNAS EN LA API DE CORTEX XDR
1. Alertas externas: Añaden un contexto mas amplio a los incidentes. Puede usar la API cortex XDR o syslog collector en Broker BM para enviar alertas desde cualquier origen externo a cortex XDR. 
2. Ingesta de alertas externas a traves de la API de cortex XDR: Para enviar alertas a la instancia de Cortex XDR a través de la API de Cortex XDR, primero genere una clave de API para la autenticación y, a continuación, prepare los atributos de alerta en un archivo con formato JSON para realizar una llamada a la API.
   - Generar clave API: Para generar una clave de API para la autenticación, vaya a **Configuraciones > Integraciones > Claves de API** y haga clic en **+ Nueva clave**. Tenga en cuenta que una vez generada la clave, Cortex XDR solo muestra la nueva clave de API una vez. Debe especificar su ID de clave de API, a la que se puede acceder en la tabla de claves de API en cualquier momento
   - Preparar atributos de alerta:  Para esta llamada a la API, puede preparar los detalles de la alerta en un archivo de texto con formato JSON.
     ![[Pasted image 20241210172152.png]]
 1. Depuracion de alertas insertadas exeternamente: Puede depurar alertas para obtener informacion mas detallada y especifica de los atributos sobre ellas **Anrimos menu contextual > Alerta de depuracion / debug alert**

