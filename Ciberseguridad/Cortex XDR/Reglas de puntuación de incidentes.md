#Nodo
Podemos priorizar y resaltar automaticamente sus incidentes mediante reglas en la pagina de configuracion de incidentes de la consola de administracion. Todas las reglas funcionan a nivel de alerta y no directamente a nivel de incidentes. Pero la modificacion de las alertas de un incidente tambien modifica el incidente en si.
	Configuraciones de incidentes:
- Puntuacion de incidentes, puede crear reglas para puntuar incidentes
- Alertas destacadas, puedes destacar incidencias destacando sus alertas
- Campos destacados, los campos destacados contienen campos de alerta destacados

1. Puntuación de incidentes: Valor numerico asignado a un incidente para indicar la gravedad o urgencia del incidente. Metodos de puntuacion de incidentes:
   - Manual: Puede asignar puntuaciones manualmente directamente a los incidentes desde la pagina Incidentes
   - Automatico: Puede utilizar la puntuacion de incidentes para actualizar automaticamente las puntuaciones de incidentes cuando se envian alertas a los incidentes. 
   - Puntuacion inteligente: Smartscore calcula de forma automatica e inteligente las puntuaciones de los incidentes basandose en el aprendizaje automatico y el analisis estadistico.

2. Jerarquia de reglas de puntuacion: Las nuevas reglas de puntuacion se colocan en la jerarquia de reglas para proporcionar una granularidad mas precisa. Cada nueva regla tiene una regla base como principal. Si la misma alerta coincide con una o mas subreglas, la alerta tambien se puntua por cada subregla coincidente, sin embargo las subreglas solo se evaluan si coinciden sus reglas principales.

3. Gestion de puntuaciones de incidentes: En la pagina incidentes se realiza la administracion de puntuacion de incidentes con el boton derecho y desflose de la puntuacion de incidentes. 