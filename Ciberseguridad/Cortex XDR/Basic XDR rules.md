
DESCRIPCION GENERAL DE LAS REGLAS XDR
1. Reglas basadas en indicadores de amenazas personalizados: Se puede crear reglas propias XDR especificando la caracteristica de los indicadores de amenazas como criterios de regla. Para identificar los indicadores de amenazas es buscar clientes potenciales en los conjuntos de datos XDR. Alternativamente, los indicadores de amenazas se pueden obtener de flujos confiables de inteligencia de amenazas.
	1. Cortex comprueba el flujo de registros entrante con estas reglas, si hay coincidencia xdr genera alerta de deteccion con atributos como: nombre, categoria, gravedad.
	2. Cuando se genera un ataque y no se bloquea la alerta es de tipo deteccion, los ataques contra los puntos de enlace solo pueden ser bloqueados por el agente XDR, no por los componentes en la nube de las instancias XDR.

2. Tipos de reglas de CORTEX XDR: Existen reglas de XDR que podemos crear en funcion de la necesidad
	1. Indicadores de compromiso (IOC): Las reglas de IOC en cortex XDR definen las propiedades estaticas de las amenazas como nombres de archivo, rutas, hashes de archivos, ip y nombre de dopinio, su objetivo es detectar malware conocido y simple.
	2. Las reglas BIOC definen las caracteristicas de comportamiento de las amenazas, como las tacticas, tecnicas y procedimientos utilizados durante el ciclo de ataque, las reglas BIOC estan pensadas para detectar amenazas persistentes avanzadas, como ataques sin archivos.
	3. Reglas de correlacion: Deben considerarse como reglas BIOC muy avanzadas. De hecho la condicion de una regla de correlacion se define como una consulta de busqueda XQL. BIOC XQL es limitado en terminos de sintaxis XQL y conjuntos de datos disponibles, mientras que las reglas de correlacion pueden consistir en cualuier busqueda XQL que utilice casi cualquier sintaxis XQL para ejecutarse en varios conjuntos de datos.

3. Conjuntos de datos utilizados por el motor de reglas: La coincidencia de reglas se basa en dos componentes: La condicion de la regla y los flujos de registro entrantes almacenados en conjuntos de datos.
   - El motor de reglas XDR comprueba constantemente que los flujos de registro entrantres coincidan con las condiciones de la regla XDR
   - Algunos conjuntos de datos se crean para almacenar solo los registros creados por los componentes XDR, como los agentes XDR, otros se almacenan en registros de terceros.
   - Las reglas BIOC se comprueban con los conjuntos de datos xdr_data y cloud_audit_log, mientras que las de correlacion se comprueban en todos los conjuntos de datos.
   - El conjunto de datos xdr_data contiene registros y endpoints que se vinculara con registro de trafico NGFW si se proporciona la integracion



[[Reglas de IOC]]
[[Reglas de BIOC]]
[[Reglas de supresión IOC-BIOC]]

