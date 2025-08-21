#Nodo

1. Funciones de extraccion JSON: extraen valores o datos especificos de un objeto JSON. Proporcionan una forma comoda de acceder a las estructuras JSON en funcion de criterios o rutas especificos.
   
   Funciones de extraccion: XQL proporciona tres funciones de extraccion JSON, una para cada tipo de elemento de un objeto JSON. Las tres funciones de extraccion JSON son:
   - Escalar: json_extract_scalar(jsonObj, jsonScalarPath) devolviendo la cadena
   - Arreglo: json_extract_array(jsonObj, jsonArrayPath) devolviendo matriz de cadenas
   - Objeto JSON: json_extract(jsonObj, jsonObjPath) devolviendo el objeto JSON
     
    Parametros de extraccion:
    - Campo o variable de tipo JSON en XQL
    - ruta de acceso JSON que coincida con un escalar, matriz o un objeto. La ruta debe estar entre comillas dobles y coincidir con la funcion utilizada.

2. Extraccion de valores escalares: Implica aislar los valores deseados de conjuntos de datos complejos mediante el analisis, el filtrado o el acceso a claves especificas. La extraccion de valores escalares ayuda a recuperar valores individuales para su analisis o manipulacion.
   
   Aislamiento de los valores deseados: La extracción de valores escalares incluye la identificación y el aislamiento de los valores escalares deseados de estructuras de datos complejas como matrices, objetos o JSON.
   ![[Pasted image 20241213130931.png]]
   Funciones de conversion de datos XQL
   En el ejemplo, todas las variables c1, e1, y f1 son de tipo string. Si se requieren otros tipos de escalares como numbre (entero o flotante) o booleanos, use una de las funciones de conversion de datos XQL disponibles. ![[Pasted image 20241213131055.png]]
   
3. Extracting arrays: La extraccion de matrices le permite recuperar los elementos o valores especificos de las matrices dentro de sus datos. Puede extraer la informacion necesaria de la matriz especificando el indice o la condicion. 
   Matriz de extraccion JSON
   ![[Pasted image 20241213132012.png]]
   ![[Pasted image 20241213132117.png]]

4. Extraccion de objetos secundarios JSON: Los objetos secundarios JSON estan anidados dentro de otros objetos, formando una estructura jerarquica. XQL permite consultar datos de objetos secundarios JSON para recuperar datos anidados especificos dentro de una estructura JSON.
   ![[Pasted image 20241213133212.png]]
   
   **Evitar la extraccion JSON con rutas de acceso de matriz JSON**: Evite usar json_extract con rutas de acceso de matriz JSON. El motor XQL todavia puede ejecutar este tipo de consultas, pero los valores extraidos no son utiles.
   ![[Pasted image 20241213133332.png]]
   ![[Pasted image 20241213133342.png]]
