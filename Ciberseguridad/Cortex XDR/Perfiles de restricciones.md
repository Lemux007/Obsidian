#Nodo

1. Opciones de configuracion de perfil de restricciones: Los perfiles de restricciones limitan la superficie expuesta a ataques en los puntos de conexion de windows defiendiendo donde y como los usuarios pueden ejecutar archivos. Opciones de condiguracion de perfil de restricciones:
	1. Archivos ejecutables
	2. Archivos de ubicacion de red
	3. Archivos multimedia extraibles
	4. Archivos de unidad optica
	5. Reglas de prevencion personalizadas
2. restricciones en archivos ejecutables: Si usamos archivos ejecutables para limitar la ejecucion de los archivos en los discos duros, especificaremos la siguiente configuracion.
	1. Modo de accion: Especifica la ccion realizada por XDR cuando se cumplen los criterios supervisados proporcionados en este grupo.
	2. Uso predeterminado: **marcar: Use Default** Si desea utilizar la accion predeterminada para el grupo de configuraciones
	3. Archivos/Carpetas en lista de bloque: Podemos especificar la lista a bloquear.
3. Implementacion de modo de accion por parte del agente.
	1. ![[Pasted image 20241203120353.png]]
4. Restriccion en archivos ejecutables para discos no HDD: Se pueden configurar: ARchivos de ubicacion de red, archivos de medios extraibles, archivos de unidad optica. ![[Pasted image 20241203120713.png]]

