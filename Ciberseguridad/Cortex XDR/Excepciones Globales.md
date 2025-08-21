#Nodo

1. Aplicaciones de excepciones globales: Las excepciones globales se aplican incondicionalmente a todos los puntos de conexión. Como alternativa, puede navegar a **Endpoints > Policy Management > Profiles > Exceptions Profiles** y aplicar excepciones a endpoints específicos mediante reglas de política. Las excepciones en ambos ámbitos agregan todas las excepciones aplicadas.
   - Las excepciones en los perfiles de execepciones se aplican a los puntos de conexion determinados por las directivas
   - Las excepciones globales se aplican a todos los puntos de conexion sin necesidad de reglas de directiva
   - Las excepciones globales junto con las excepciones de los perfiles, constituyen la suma de todas las excepciones que se aplican a los extremos.
   - Ajusta globalmente algunas opciones de configuracion en otros perfiles.

	Creacion de excepciones globales: Para crear una excepción global, vaya a **Administración de políticas > Prevención > Excepciones globales**. Esto se utiliza para las excepciones de proceso y soporte.
	
