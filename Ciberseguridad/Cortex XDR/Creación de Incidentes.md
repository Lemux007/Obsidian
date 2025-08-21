#Nodo

1. Resumen de incidentes: Un incidente es un ataque unico e independiente
   - Un incidente es un objeto contenedor para agrupar alertas, activos y artefactos relacionados.
   - Alertas son objetivos de notificacion para informar actividades o eventos sospechosos
   - Activo, los recursos son los nombres de los puntos de conexion y los usuarios afectados
   - Los artefactos son atributos de objetos atacantes, como nombres de archivos, firmantes de archivos, procesos, dominios y direcciones ip
   - Cada alerta esta asociada a un ID de alerta, por lo tanto las alertas relacionadas se agrupan en el mismo incidente. 

2. Alertas de enlace a incidentes coincidentes: Los atributos ciberneticos relacionados con la seguridad o el ataque incluyen el ID de causalidad, direccion ip y nombre del archivo del proceso.
   Proceso basico de alertas:
   - Extraer, los atributos ciberneticos de la alerta
   - Buscar, el incidente coincidente mediante atributos ciberneticos
   - Atar, si se encuentra un incidente vincule la alerta al incidente coincidente.
   - Crear, Si no hay incidente cree uno nuevo

	Alertas coincidentes: XDR compara alertas dentro de un incidente en funcion de sus atributos ciberneticos, por lo tanto estas estan relacionadas. 

3. Creación de nuevos incidentes: XDR crea un nuevo incidente, a partir de las siguientes coindiciones:
   - Coincidencia encontrada
   - No se encontro coincidencia
	Alertas de creacion de incidentes: 
	- Incidentes con muchas alertas: XDR limita el numero de alertas en un incidente para evitar la inanicion de los demas incidentes.
	- Alertas medias, altas o criticas: Estas son las unicas que conducen a la creacion de un nuevo incidente. 
	- Alertas recurrentes: XDR elimina el ruido en los incidentes al agregar alertas recurrentes en una sola alerta
