#Nodo

1. Componentes del flujo de ingesta: El flujo de ingesta de Cortex XDR consta de Cortex XDR, un componente en la nube, y tres componentes locales, entre los que se incluyen Broker VM Syslog Collector, Broker VM y XDR Collectors.
   ![[Pasted image 20241210165247.png]]
- Recopilación de registros desde la nube: Los proveedores de nube pública, como AWS, Azure y GCP, pueden enviar varios tipos de registros a Cortex XDR. Los registros del proveedor de nube incluyen los tipos de red, flujo y auditoría. Para recopilar registros de la nube, es necesario configurar tanto la nube proporcionada como la consola de administración de Cortex XDR
- Recopiladores locales: En las instalaciones, las máquinas virtuales de Broker y los recopiladores de XDR pueden recopilar varios tipos de registros, incluidos los registros de eventos de punto final. Estos componentes también pueden funcionar como motores de reglas de análisis. Se pueden adjuntar varias instancias de VM de Broker e instancias de XDR Collector a la misma instancia de XDR. Además, la máquina virtual de Broker proporciona varios componentes dedicados (también conocidos como applets) para recopilar registros de esas aplicaciones conocidas, como bases de datos relacionales, servidores FTP, servidores HTTP y cualquier registro con formato CVS en las carpetas compartidas.

2. Reglas de analisis: Las reglas de análisis de Cortex XDR forman parte del flujo de ingesta de datos de Cortex XDR. Un motor de reglas de análisis analiza una entrada de registro sin procesar, aplica la lógica de regla a los campos de registro de entrada de análisis y, a continuación, prepara y devuelve una o varias filas para agregarlas a los conjuntos de datos. Las reglas de análisis se compilan en la instancia de Cortex XDR y, a continuación, se pasan a las instancias de Broker VM y XDR Collector conectadas.
   - Proposito de las reglas de analisis: Eliminar datos irrelevantes de los registros sin procesar entrantes. Beneficio neto de organizar y limpiar los registros antes de almacenarlos es doble:
     - Reduccion de datos ahorra espacio de almacenamiento
     - Conjuntos de datos minimizados y organizados de forma eficaz mejoran el rendimiento de las consultas XQL.
 - Autorizacion para analizar reglas: Un usuario debe ter+ner privilegios de administrador de cuentas y administrador de instancias de cortex XDR
