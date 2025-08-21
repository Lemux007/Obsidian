#Nodo

1. Descripcion general de join stage: En cortex XQL, la etapa de union combina datos de varios origenes en funcion de una condicion o clave especificada. Al definir la condicion de union, puede consolidar y correlacionar datos de diferentes origenes, lo que permite un analisis mas completo, el enriquecimiento de datos y la informacion contextual. 
   Ejemplo de consulta de la fase de union: XQL proporciona la fase de union para estas operaciones de correlacion. Ejemplo de consulta que incluye una fase de combinacion de la siguiente manera:
   ![[Pasted image 20241216133108.png]]
   
   En una consulta XQL con una combinacion se utilizan dos etapas del conjunto de datos. Una consulta de este tipo contiene una consulta incrustada y la fase de union viene con su propia consulta XQL, como join(dataset=my_event_desc).
   ![[Pasted image 20241216133251.png]]
   
2. Etapa de union de XQL: Asocia diferentes conjuntos de datos. La fase de combinacion combina los conjuntos de resultados en un unico conjunto de resultados. Este conjunto combinado se utiliza en las fases posteriores de la consulta principal. 
   Similitudes de XQL con SQL
   
   **Similitudes de XQL con SQL**: La terminologia utilizada en XQL proviene principalmente de la jerga SQL. Al utilizar etapas de union, estan disponibles opciones como "el tipo es la izuierda" o "conflict_strategy es la derecha". En SQL, el termino "izquierda" se refiere al conjunto de resultados principal, mientras que "derecha" se refere al conjunto de resultados de combinacion creado por la propia etapa de combinacion mediante la ejecucion de su propia consulta.

3. Clausulas de fase de union: Las clausulas son bloques de construccion o componentes constitutivos de etapas; Las clausulas pueden ser obligatorias u opcionales.
   La fase unioncombina las columnas (campos) de los dos conjuntos de resultados. Sin embargo los conjuntos de resultados pueden tener campos con el mismo nombre, posiblemente con valores diferentes, por lo tanto puede producirse un conflicto de nombres durante la combinacion. Los valores posibles son izquierda y derecha para resolver el conflicto. 
   Izquierda: El conjunto combinado muestra solo FLD del conjunto de resultados principal
   Derecha: El conjunto combinado solo FLD del conjunto de resultados de union.
   Ambos: Ambos campos se copian en el conjunto combinado que muestra el FLD del conjunto principal tal cual y el FLD del conjunto de union bajo el nombre JOIN_FLD
   
4. Ejemplos de consultas XQL: Las consultas de union de XQL pueden variar en complejidad, y algunas tienen etapas de combinacion minimas, mientras que otras son mas elaboradas. 
   Se requieren tres clausulas: Query, as y condition, LA consulta de combinacion dataset= my_event_desc, la clausula de as e y la condicion de combinacion es e.type = event_type
   ![[Pasted image 20241216140003.png]]
   
   En esta consulta, vera una clausula de consulta de combinacion con tres etapas: conjunto de datos, filtro y campos
   ![[Pasted image 20241216140054.png]]
   
   **Consulta de combinacion tipica**: 
   ![[Pasted image 20241216140159.png]]
   
   **Join Stage with all options / unirse al escenario con todas las opciones**: En este ejemplo se muestra una fase de combinacion con todas las clausulas obligatorias y opcionales. Si se establece el tipo de combinacion a la derecha, se asegurara de que el conjunto de resultados tenga todos los registros del conjunto de resultados de la consulta de combinacion (Tambien conocido como conjunto de resultados derecho)
   ![[Pasted image 20241216140454.png]]
   
5. Flujo de ejecución de consultas XQL: La fase de flujo XQL abarca varios pasos, que incluyen la ejecucion, la recuperacion y la preentacion de los resultados de la consulta. 
   **Etapas de flujo XQL**: Conceptualmente, las etapas de XQL se ejecutan secuencialmente, pero la implementacion fisica puede variar. La generacion del conjunto de resultados comienza al principio de la ejecucion de la consulta. 