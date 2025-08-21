#Nodo

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
   