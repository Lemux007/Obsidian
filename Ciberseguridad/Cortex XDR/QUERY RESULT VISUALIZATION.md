#Nodo

1. Pestaña resultados de la consulta: Cortex XSIAM coloca los resultados de la ejecucion de una consulta XQL en un conjunto de resultados. Hay varias maneras de mostrar el contenido del conjunto de resultados. 
   - Pagina de busqueda de XQL: Puede editar y ejecutar consultas XQL en la pagina Busqueda XQL de la consola de administracion
   - Modos de visualizacion: Se colocan tres modos de visualizacion como botones de accion en la esquina superior izquierda
   - Modo de mesa: De forma predeterminada el modo Tabla es abierto, muestra los resultados de la ejecucion
   - Panel campos contraibles: Muestra todos los campos como la tabla de resultados como elementos en los que se puede hacer clic en una lista vertical.

2. Modos de visualizacion: 
   - Tabla: La predeterminada, muestra los resultados de las consultas, se muestran en el modo visualizacion tabla en forma de tabla, filas y column
   - Avanzado: A diferencia de tabla muestra dos apartados mas: _Time y event_
   - Grafico: El modo grafico permite ver los resultados en un grafico distinto ya sea paste,l mapas, 
     
     Diferencias entre tabla y avanzado:
     Tabla:
     ![[Pasted image 20241216121951.png]]
     Avanzado:
     ![[Pasted image 20241216122005.png]]
     
     Formatos de registro: RAW, JSON y TREE

3. Panel campos: El uso principal de panel campos es analizar los valores de un campo mediante un histograma. El panel campos esta disponible en las vistas Tabla y avanzado
   **Histograma**: Muestra todas las columnas de la tabla de resultados en la lista de campos verticales, pero si se hace clic en un campo de tipo JSON o si el campo contiene datos compuestos (Matriz de algunos tipos), obtendra el siguiente error "El campo solicitado no es compatible"
   
4. Cuadro de dialogo Histograma: Un histograma es una tabla de tres columnas: Valor, recuento y porcentaje. Estas columnas de histograma son las mismas para todos los campos de la tabla de resultados y no cambian. Tenga en cuenta que se crea una tabla de histograma para el campo seleccionado
   - Columna valor: muestra varios valores del campo seleccionado, un valor por pila. Por lo tanto system que es el unico valor que vimos en la tabla de resultados regular, tambien aparece en VALUE en la tabla de histograma.
   - Columna de recuento: Muestra la frecuencia de cada valor visto en la tabla de resultados. El sistema se encuentra en 895 filas diferentes, que es uno de los valores de campo de proceso para esta consulta.
   - Columna de porcentaje: Muestra la relacion entre cada valor de la tabla de resultados y el numero total de filas. El numero total de filas no se muestra en la captura de pantalla.
     ![[Pasted image 20241216125326.png]]
     
---
# RESULTADOS DE LA CONSULTA EN GRAFICOS
1. Visualizacion en graficos: El modo grafico muestra los resultados de la consulta en uno de los varios tipos de graficos disponibles: se utiliza el editor de graficos para especificar parametros del grafico, incluidos el tipo de grafico, el encabezado, los datos, el color, la fuente y la leyenda. 
   
   Ejemplo de consulta: LA consulta obtiene el codigo de pais asociado a la direccion IP en el campo action_remote_ip y a continuacion cuenta las ocurrencias de eventos por pais. 
   ![[Pasted image 20241216130427.png]]
   
   Tipo de grafico: Mapa, columna. Dependiendo de los tipos de datos que se retornen es el grafico que mas conviene utilizar.

2. Incrustar la configuracion del grafico en las consultas: Puede codificiar la configuracion del modo Graph directamente en la consulta XQL mediante la fase de vista. A continuacion, cuando se ejecuta el codigo que incluye una fase de vista, el modo de visualizacion de graficos se activa automaticamente. 
   
   Formas de usar la fase de vista: 
   - Ver grafico
   - Ver lo mas destacado
     
    Códigos de consulta con tipo de grafico y etapa de vista: En este ejemplo de XQL se explora el uso de codigos de consulta junto con el tipo de grafico y la fase de vista.
    En este ejemplo observe la etapa de vista y como modifica los parametros Graph, Al ejecutar esta consulta, no es necesario ir al modo grafico, ya que la pestaña resultados de la consulta la activara automáticamente.
    ![[Pasted image 20241216131433.png]]![[Pasted image 20241216131449.png]]
    
    
    