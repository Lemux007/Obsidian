#subnodo
PUNTO DE VISTA DE CAUSALIDAD
1. Escenario de ataque: Un analista de SOC supervisa continuamente las alertas y los incidentes en la consola de gestion de XDR. Considere el siguiente escenrio de ataque sobre una alerta causada por un usuario final y la investigacion que sigue.
   **Alerta que provoca una accion del usuario final**: Un usuario final inexperto y desprevenido hace doble clicl en un archivo en su punto de conexion lo que hace que ejecute un archivo que contiene un script malintencionado. 
   **Accion de investigacion**: un analista que trabajaba en el incidente se dio cuenta de que el script era tipo Visual Basic (VB) que llamaba a algunas apps legitimas de windows.
   **Investigacion de atributos de alerta**: El analista observa algunos atributos de alerta.
   
   Areas de investigacion: 
   - Procesos involucrados en el ataque: Identifique todos los demas procesos implicados en el ataque, junto con sus cadenas de ejecucion completas.
   - Recursos afectados: Identifique los procesos maliciosos que pueden haber modificado algunos archivos, creado otros nuevos o incluso eliminado algunos.
   - Cronologia de eventos: Identifique las escalas de tiempo de los eventos de ataque durante el periodo de actividad.

- Analisis casual: Tipo de analisis estadistico de datos de eventos 8Alertas y registros) para descifrar las relaciones causa-efecto entre los atacantes
- Analisis del la linea de tiempo: El analisis de la linea de tiempo muestra a los atacantes y sus vicitmas en una sola linea del tiempo.

2. Acciones de tarjeta abierta: Mestra los resultados del analisis causal de una alerta en una vista especial llamada vista de causalidad
   Disponibilidad de acciones de tarjeta abierta: 
   - Alertas cosidas: El punto verde indica que estab habilitadas para alertas vinculadas o cosidas
   - Alertas no vinculadas con info limitada: Acciones de tarjeta abierta siguen disponibles para alertas generadas por el agente XDR, pero la vista de causalidad proporciona datos muy limitados si la alerta generada por XDr no esta vinculada
   - Alertas no vinculadas sin informacion: LAs acciones abrir tarjeta no estan disponibles para las alertas no vinculadas que son generadas por el agente XDR



GRAFICO DE INSTANCIAS DE CAUSALIDAD
1. Leyenda de nodos de proceso: Un nodo de proceso se simboliza mediante un circulo y proporciona informacion sobre el numero, la etiqueta CGO, el nombre de usuario y el nombre del nodo de proceso de los nodos en el CI.
   - Nombre de usuario
   - Nodo seleccionado
   - Numero de nodo
   - Etiqueta CGO
   - Nombre del nodo de proceso

2. Nodos de alerta, usuario e inyeccion: Puede encontrar otros tipos de nodos, como nodos de alerta, usuarios e inyeccion.
   - Nodos de alerta: Mientras que un nodo de proceso representa un unico proceso del SO, un nodo de alertas se asocia a un nodo de proceso especifico que provoco que se generaran las alertas.
   - Nodo de usuario: Representa a los usuarios en el grafico de CI y muestra informacion detallada del usuario, como el grupo de AD
   - Nodo de inyeccion: Puede ser un sibtipo de nodo de proces, es el tipo de todo de proceso con informacion adicional sobre la inyeccion del codigo y las llamadas RPC.
     
	Eventos de inyeccion y no inyeccion: Un nodo de inyecccion (Proceso) tiene dos partes diferentes en las que al hacer clic: inyeccion y no inyecion. Cada parte tiene sus propias tablas de eventos, pero ambas apuntan al mismo proceso del SO.

VISTA DE LINEA DEL TIEMPO
1. Diseño de vista de linea de tiempo: Es un panel dividido con paneles en la parte superior e inferior de la pagina separados por un divisor arrastrable, secciones del panel.
   - Eventos
   - Escala del tiempo
   - Nodos de eventos
   - PRocesos
	Panel inferior: muestra una tabla de eventos asociados con el nodo seleccionado. 

2. Secciones de la vista de la linea de tiempo: Puede utilizar la escala de tiempo, la seccion de eventos y las marcas de tiempo de eventos para ver eventos en la lienea del tiempo.
   - Seccion de escala de tiempo: Se muestra un periodo de 24hrs, proporciona botones para 7dias
   - Seccion de eventos: Se enumeran todos los tipos y categorias de alto nivel de eventos identificados durante el ciclo de ataque. tres categorias de lto nivel: XDR en rojo, alertas BIOC y correlacion en naranja y otras actividades y eventos informativos en azul.
   - Seccion de tiempo de eventos: La proyeccion horizontal de los eventos y la proyeccion vertical de la linea del tiempo se intersectan en un punto que representa un nodo de eventos
     
    Alertas informativas: No se activan como un indicador de ataque ni se envian a los incidentes, no se enunmeran en la tabla de alertas de la pagina de alertas y no se muestran en la vista de causalidad
    Ejecucion de procesos: Es un tipo de actividad informativa que puede ser aprovechada maliciosamente por los atacantes. 
