#Nodo
Descripcion general de BTP: BTP es un modulo de proteccion posterior a la ejecucion para detectar de forma inteligente ataques sofisticados mediante la supervision continua de la acvividad de endpoints. y actividad con una lista de reglas predefinidas conocidas como reglas BTP. ![[Pasted image 20241204093719.png]]
2. Tipos de ataque detectados por BTP: BTP esta diseñado para detectar y prevenir ataues basados en scripts.
	1. Deteccion: Detecta patrones de ataques en scripts
	2. Analisis continuo: Analisa continuamente los flujos de actividades en curso para detectar ataques.
3. Reglas BTP: una regla BTP es un conjunto de operaciones predefinidas y agrupadas lógicamente en los recursos que los atacantes aprovechan con frecuencia. Por ejemplo una regla puede constar de operaciones como deshabilitar la seguridad UAC de windows, crear archivos ocultos en system32 y crear un proceso secundario.
	1. Operaciones maliciosas: 
	   ![[Pasted image 20241204094404.png|400]]
4. Configuracion BTP: Posible habilitar la cuarentena de archivos malintencionados para poner en cuarentena el malware detectado por BTP.
	1. BTP puede detectar intentos de cargar controladores vulnerables en puntos finales de windows.
	2. Puede usar archivos/carpetas en la lista de permitidos para especificar procesos que BTP nunca termina, independientemente de las reglas 