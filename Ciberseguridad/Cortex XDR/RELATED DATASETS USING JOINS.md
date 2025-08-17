# JOIN STAGE BASICS
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
---
# TIPOS DE UNION
1. Uso de combinaciones en lenguajes de consulta: Las uniones combinan datos de varias tablas en funcion de columnas relacionadas. Las operaciones de combinacion cruzada como esta, tambien conocidas como productos cartesianos, son importantes en XQL para analizar datos de diferentes tablas. 
   **Unir variantes**: Comprender el producto cartesiano es la clave para comprender los tipos de union XQL. En este contexto, el termino "producto" es el resultado de la multiplicacion y no tiene nada que ver con los productos de consumo.
   - Producto cartesiano: AxB
   - Tipos de combinacion en lenguajes de consulta: Conjuntos de productos cartesianos reducidos (Anular la seleccion de los registros no coincidentes en el producto cartesiano)
   - Diferencias entre los tipos de union QL: Combinacion cartesiana o cross join.
     
    Conjunto de datos de consulta: Para comprender los tipos de combinación de XQL, consideramos los dos conjuntos de datos simples que se describen a continuación. 
    Tabla de la izquierda: LT, significa la tabla de la izquierda
    Tabla de la derecha: RT, significa la tabla de la derecha.
    
    Union cartesiana: Dadas dos tablas LT y RT, la union cartesiana se crea emparejando cada fila de la tabla LT con todas las filas de la tabla RT. Si dos tablas tiene n y m filas, la combinacion cartesiana tiene n*m filas. 

2. UNION DE TIPO INTERNO (inner join): Una combinacion de tipos interno devuelve todos todos los registros que coinciden con los valores de los conjuntos de resultados izquierdo y derecho. El diagrama de Venn ilustra el tipo interno como la interseccion de dos conjuntos. La combinacion interna de XQL es equivalente a SQL join o conocida como inner join. ![[Pasted image 20241216161755.png]]
   ![[Pasted image 20241216161716.png]]

3. Union de tipo izquierdo: Devuelve todos los registros del conjunto izquierdo, asi como los registros coincidentes del derecho. 
   ![[Pasted image 20241216161818.png]]
   ![[Pasted image 20241216161738.png]]
   
4. Right type join: Una combinacion de tipo derecho devuelve todos los registros del conjunto derecho, asi como los registros coincidentes de la tabla izquierda.![[Pasted image 20241216161943.png]]
   ![[Pasted image 20241216161953.png]]
   
   