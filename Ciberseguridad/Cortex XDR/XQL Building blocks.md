# ETAPAS DE XQL
1. Etapas de una consulta: Las etapas son los bloques de creacion basicos de una consulta XQL. Una consulta XQL consta de una o varias fases separadas por una barra vertical (|), el simbolo delimitador de fase. Algunas de las etapaps de una consulta XQL son el conjunto de datos, los campos, el filtro, la combinacion, la ordenacion y la modificacion.
   - Etapas para la realizacion de operaciones: Cada fase realiza una operacion determinada en la evaluacion de consultas. Entre los ejemplos de operaciones se incluyen la configuracion del conjunto de datos, el filtrado, la especificacion de campos, la ordenacion y la limitacion.
   - Etapas para generar declaraciones: A diferencia de las fases de filtro y modificacion, algunas fases solo generan declaraciones para el motor de consultas XQL. Por ej la fase del conjunto de datos indica al motor de consultas XQL que conjuntos de datos usara la consulta para ejecutarse.

2. Parametros en etapas: Todas las etapas requieren algunos parametros para funcionar. El tipo y el orden de los parametros varian segun la etapa. En los ejemplos siguientes se muestran los usos de parametros en XQL. 
   - Conjunto de datos / dataset: *dataset = xdr_data*
   - Filtro / Filter: *filter actor_process_image_name = "powershell.exe"*
   - Fields / campos: *fields event_type, event_sub_type as SUBTYPE*
   - Limit / limites: *limit 4*

3. Etapa de configuración: La etapa de configuracion establece dos parametros clave que afectan a la forma en que el motor de consultas XQL interpreta y ejecuta una consulta; la etapa de configuracion es opcional. Aunque la consulta puede constar de solo una fase, como la fase del conjunto de datos, la fase de configuracion no puede ser la unica fase de una consulta.
   Parametros de la etapa de configuracion:
   - Distinguir entre mayusculas y minusculas y tiempo de compilacion
   - Periodo de tiempo.

	Ajuste fino de la etapa de configuracion:
	config case_sensitive = verdadero \ falso
	config timeframe = (numero)(unidad de tiempo)
	
	Ejemplos de etapas de configuracion: En este eejemplo el motor de consultas devuelve registros de las ultimas 24hrs con el atributo actor_process_image igual a powershell
	*config* timeframe = 24h | *filter* actor_process_image_name = "powershell.exe"
	
	En este segundo ejemplo, el intervalo de tiempo de consulta se establece en un intervalo especifico con marcas de tiempo de inicio y finalizacion definidas.
	*config* timeframe between "2021-04-01 00:00:00" and "2021-12-31 00:00:00"

	XQL configuration setting: XQL tiene una configuracion en todo el sistema para controlar la distincion entre mayusculas y minusculas en todas las consultas. **Configuraciones > Configuracion general > del servidor**

4. Etapas del conjunto de datos: La ejecución de una consulta XQL en Cortex XSIAM procesa los registros de una fuente de datos específica denominada conjuntos de datos. La etapa del conjunto de datos es una instrucción opcional para que el motor XQL procese los registros de datos seleccionados. Si no se especifica ningún conjunto de datos en la consulta, el motor asociará las ejecuciones de la consulta con el conjunto de datos predeterminado, xdr_data. Este conjunto de datos está disponible en todas las instancias de Cortex XSIAM, independientemente del tipo de licencia. Para cambiar el conjunto de datos predeterminado, vaya a **la sección CONFIGURACIONES > Administración de datos > Administración de conjuntos de datos**.
   
   Sinopsis de la etapa del conjunto de datos: Implica la seleccion de fuentes de datos para el analisis. Esto incluye repositorios de registros, dispositivos de red o dispositivos de seguridad que contienen datos relevanets
   
   dataset = (nombre del conjunto de datos)                               dataset in (lista de datos separadas por comas)
   Ejemplos:
   dataset = xdr_data                                                                     dataset in (xdr_data, onelookup)

5. Etapa objetivo: La etapa de destino guarda el conjunto de resultados en un conjunto de datos de destino. El conjunto de datos de destino se puede crear de nuevo o agregar a un conjunto de datos existente. Si se utiliza, la fase de destino debe ser la última de una consulta. Solo puede descargar tipos de búsqueda en la consola de administración de Cortex XSIAM en Administración de conjuntos de datos. El conjunto de datos de tipo no tiene ninguna acción de descarga en el menú contextual.
   
   - Sinopsis de la etapa objetivo: En la fase de destino, se especifican los elementos de datos que se van a extraer, analizar o manipular.
     target type=dataset | lookup append=true | false (dataset name)
   - Ejemplo de la etapa objetivo: La consulta de este ejemplo se usa para guardar el conjunto de datos DL3 como DL4 con una diferencia: el campo CNT en DL3 es una cadena y se convierte en un entero en DL4.
     dataset = DL3 
     | alter CNT = to_integer(CNT) 
     | target type = dataset DL4

6. Etapa de campos: especifica una lista de campos que forman las columnas de la tabla de resultados. Los campos disponibles varian en funcion del conjunto de datos
   
   Sinopsis de la etapa de los campos: Las consultas XQL se forman en etapas, cada una de las cuales realiza una operación de consulta específica. La sintaxis de cada fase incluye expresiones representadas por campos, valores, operadores y lógica booleana para formular una consulta
   ![[Pasted image 20241212173824.png]]
   
   Ejemplo 1 de la etapa de campos: 
   ![[Pasted image 20241212173836.png]]
   
   Ejemplo 2: Esta consulta incluye dos etapas de campo. La primera etapa del campo se omite porque el segundo campo la invalida. La segunda etapa de campo para la exclusión de campo se omite porque no se especifica un guión en la etapa.
   ![[Pasted image 20241212174109.png]]

7. Etapa de filtrado: La etapa de filtro selecciona los registros (registros) que se incluirán en el conjunto de resultados, determinando las filas de la tabla de resultados. Cada fase de filtro evalúa una expresión booleana para cada registro del conjunto de datos como verdadera o falsa. A continuación, los registros con valores verdaderos se agregan al conjunto de resultados.
   
   Sinopsis de la etapa de filtro: Para filtrar datos, establezca condiciones para restringir el conjunto de datos y centrarse en eventos específicos que cumplan determinados requisitos. Esto refina el conjunto de datos para su posterior análisis.
   ![[Pasted image 20241212174417.png]]
   Ejemplos: En este ejemplo, el operador "in" comprueba un elemento de una lista y devuelve true si la lista contiene el elemento.
   ![[Pasted image 20241212174455.png]]
   El operador "in" se puede expandir o reescribir de manera equivalente de la siguiente manera:
   ![[Pasted image 20241212174512.png]]
   
8. Etapas de filtro frente a campos: Las etapas de filtro y campos dan forma al conjunto de resultados; La etapa de filtro especifica las filas de la tabla, mientras que la etapa de campos especifica las columnas de la tabla
   
   Ejemplo de etapas de filtro frente a campos:
   ![[Pasted image 20241212174819.png]]
   ![[Pasted image 20241212174831.png]]

9. Etapa de edicion o Alteracion: La fase de modificación asigna valores a los campos para su uso en fases posteriores. Esta etapa crea un nuevo campo si el campo especificado no existe. ![[Pasted image 20241213091441.png]]
   Ejemplo: Se asigna una nueva variable, timeDay, al dia del mes de la fecha de creacion del registro. A continuacion, la etapa de campos informa al motor de consultas XQL de que todos los campos disponibles y el timeDay recien introducido se mostraran en la tabla de resultados. Por ultimo la fase de filtro selecciona los registros creados en los dias 1,4, 6 de cualquier mes.
   ![[Pasted image 20241213091857.png]]
   
   Aunque no produce ningún resultado útil, la siguiente consulta sigue siendo válida. Observe cómo se utiliza una fase de modificación para crear dos nuevos campos. A continuación, los campos se muestran en la tabla de resultados mediante una etapa de campos. ![[Pasted image 20241213092105.png]]
   ![[Pasted image 20241213092123.png]]
   
10. Etapa comp: La etapa comp realiza funciones de agregación en el conjunto de resultados. En esta fase se dividen las filas del conjunto de resultados en grupos según los valores combinados de la combinación de campos especificada y, a continuación, se aplica la función de agregación especificada a cada grupo. Las funciones de agregación incluyen avg, count, earlyliest, max, min y sum.
    primero ubique la palabra clave "por" que separa las dos listas de campos. La segunda lista después de "por" se utiliza para agrupar las filas de la tabla de resultados. Cada grupo se puede identificar de forma única en función de la combinación (campo1),(campo2)
    ![[Pasted image 20241213092559.png]]

    En este ejemplo se muestra como obtener el total de cargas y descargas de red por proceso. la primera etapa (filtro) filtra solo los registros para los eventos network. La segunda etapa (campos) selecciona la columna; solo se seleccionan 3 columnas  y se asignan alias con nombres descriptivos.
    ![[Pasted image 20241213095639.png]]

11. Otras etapas de XQL: Ademas de las fases descritas en las secciones anteriores, hay otras fases que se pueden utilizar en una consulta XQL, como organizar filas en el conjunto de resultados.
    - Limit: Numero maximo de entidades en resultados
    - Sort: ordenar las entidades
    - dedup: Remover valores duplicados en campos especificos
      
      Considere la desduplicación en dos fases. En la primera fase, los registros del conjunto de resultados se ordenan por el campo de ordenación (el campo después de "por") en el orden ascendente o descendente especificado.
      En la segunda fase, solo se conserva la fila superior por combinación única (campo1),(campo2), ..., mientras que se descartan otros registros con la misma combinación (campo1),(campo2), ....
      ![[Pasted image 20241213101113.png]]
      En el ejemplo, observe que la combinación de campos event_type y event_sub_type es el identificador único (también conocido como clave compuesta) de la tabla de resultados. Además, tenga en cuenta que el número de registros del conjunto de resultados es 4 y que el conjunto de resultados se ordena por EVENT_TYPE en orden descendente.
      
      ![[Pasted image 20241213101313.png]]
      
12. Ultimas caracteristicas adicionales de XQL: Capacidad de ordenar campos por columna y la adicion de la etapa getrole para enriquecer eventos. 

---
# ORDEN DE LA ETAPA
1. La importancia del orden de las etapas en XQL:
   La etapa de modificación crea un nuevo campo (una variable), timeDay. Sin embargo, la etapa fields borra todos los campos y variables definidos anteriormente. Por lo tanto, Cortex XSIAM muestra el mensaje de error "timeDay no es un valor válido" en el filtro de la última etapa
   ![[Pasted image 20241213102037.png]]
   Correcto:
   ![[Pasted image 20241213102049.png]]
   
   - Config se agrega antes de todo, no despues
     ![[Pasted image 20241213102144.png]]
     