#Nodo

1. Las reglas de directiva se utilizan para asociar perfiles a los endpoints., los perfifles asociados a una regla se consideran como la carga de una regla de politica para transmitirla a los puntos de conexion de destino.
	1. Componentes de la regla directiva: nombre de regla unico, lista especifica de puntos de conexion y lista de perfiles con un perfil para cada tipo de perfil admitido.
	2. Orden de las reglas: El orden es importante porque XDR evalua las reglas de arriba a abajo y la primer regla se aplica como la regla de politica activa.

2. Reglas de directiva predeterminadas: lista para usar todos los terminales registrados con una regla de politica predeterminada por plataforma.
3. Creacion de reglas de directiva: **Endpoints > Policy Management > Prevention > Policy Rules** Damos click en +Agregar directiva y seleccionamos Crear nueva
	1. Generalidades: Especificar: Nombre de directiva, platforma, seleccionar los perfiles creados anteriormente para cada tipo de perfil. 
	2. Objetivo: Se especifica el ambito o cobertura de la regla en forma de puntos de conexion de destino mediante filtros o seleccionando los edps manualmente.
	3. Resumen: De las especificaciones, dar listo.
	4. Guardar: Una vez agregada la regla de directiva en la tabla de reglas de directiva de prevencion, damos en guardar.
