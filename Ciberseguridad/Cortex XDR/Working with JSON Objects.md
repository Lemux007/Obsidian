# CAMPOS Y VARIABLES JSON
1. Orígenes de campos y variables JSON: Hay dos orígenes para los objetos JSON (notación de objetos JavaScript) en las consultas XQL: los campos JSON en conjuntos de datos resumidos (registros recopilados) y las variables de tipo JSON creadas explícitamente en las consultas XQL.
   Los conjuntos de datos digeridos pueden tener campos JSON. Por ejemplo, XDR_DATA tiene muchos campos JSON, incluidos action_file_device_info, agent_interface_map, http_data login_data.
   ![[Pasted image 20241213121128.png]]
   
   Variables de tipo JSON creadas en consultas XQL: Algunas funciones XQL tambien pueden devolver variables de tipo JSON. Estas funciones son object_create(), json_extract() y to_json_string(). Por ejemplo, object_create() puede crear un objecto JSON y devolver su referencia, como se muestra en el ejemplo. ![[Pasted image 20241213121712.png]]
   
   Antes de que xdr_data de campos json puedan usarse como variables json en XQL deben convertirse mediante to_json_string()
   ![[Pasted image 20241213121726.png]]
2. Tipos de datos JSON es un formato de archivo que consta de todos los pares atributo-valor serializables y legibles por humanos. La cantidad de metadatos se minimiza, lo que los hace populares para la tranmision de datos.
   Atributos JSON: pueden ser de los siguientes tipos de datos: null, numbre, string, boolean, objeto json y una matriz de otros tipos.
   - Dos puntos y comas: Un atributo se separa de su valor mediante dos puntos(:), por ejemplo "atrr1:value", las comas separan dos pares atributo-valor
   - Llaves: Cuando una coleccion de pares atributo-valor separados por comas esta encerrada por lalves {}, se denomina objeto o objeto JSON como: "{attr1:value, attr2:value2}". Un objeto tambien puede ser el valor de otro atributo, como "attr3:{attr1:value1, attr2:value2}".
   - Corchetes: Los elementos de la matriz estan separados por una coma y entre corchetes ([])
     ![[Pasted image 20241213122346.png]]
 
3. Metodos para acceder a JSON en XQL: En XQL, puede acceder a los objetos JSON mediante uno de dos metodos alternativos: funciones XQL especializadas en el procesamiento JSON y sintaxis XQL nativa en formato sugar sintactico
   - Funciones de procesamiento JSON: La operacion principal para acceder a un objeto JSON en XQL es extraer ciertas partes del objeto, las partes relevantes pueden ser de tipo cadena, matriz, o un objeto JSON interno. XQL proporciona funciones de extraccion JSON para cada tipo, json_extract_scalar(), json_extract_array() y json_extract() respectivamente.
     ![[Pasted image 20241213124122.png]]

4. JSONPath es un conjunto de expresiones que definen rutas de acceso a los elementos de los objetos JSON. JSONPath es un lenguaje con una gramatica definida y es muy similar a XPath de XML
   Notacion de puntos: 
   ![[Pasted image 20241213124357.png]]
   Notacion de corchetes:
   ![[Pasted image 20241213124456.png]]
   
5. Extraccion de XQL JSON: XQL admite notaciones JSONPath en funciones de extraccion JSON. La consulta tiene varias etapas alter, cada una con una llamada a json_extract_scalar(). Las variables con nombres que comiencen con la misma letra deben tener valores coincidentes al ejecutar la consulta.
   Notacion de consulta XQL.: Estos pares de variables se establecen mediante la función json_extract_scalar, cuyo primer y segundo parámetro son los mismos con una diferencia: el primer parámetro es idéntico en todos los casos. Por el contrario, el segundo parámetro viene dado primero por la notación de puntos y luego por la notación de paréntesis, pero ambas notaciones apuntan al mismo elemento
   ![[Pasted image 20241213125102.png]]
   ![[Pasted image 20241213125231.png]]
   ![[Pasted image 20241213125758.png]]

---
# ACCESING JSON USING EXTRA FUNCTIONS
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

---
# CCESO A JSON MEDIANTE EL FORMATO SUGAR SINTACTICO
1. Fromato sintactico de azucar: El azucar sintactico es una notacion abreviada que simplifica el acceso y la manipulacion de objetos JSON. El formato sintactico sugar permite un manejo mas facil y conciso de los elementos de la matriz dentro de la consulta XQL.
   **Hacer referencia a objetos JSON**: XQL proporciona un formato de azucar sintactico para acceder de forma nativa a objetos JSON como parte de la sintaxis del lenguaje. Deje que jsonObj y jsonPath sean una variable de tipo JSON y un literal de cadena para la ruta de acceso, respectivamente. A continuación, XQL considera jsonObj->jsonPath como otra variable que hace referencia al elemento interno de jsonObj.
   
   En el ejemplo se muestra dos formas equivalentes de hacer referencia al elemento secundario A. para una comparacion simple, root->A≡json_extract_scalar(root,"$.A"). Observe como los parametros de json_extract_scalar() para la referencia del formato sugar. 
   ![[Pasted image 20241213134521.png]]
   
2. Formato sintactico de azucar para escalares: XQL puede usar el formato sintactico sugar para hacer referencia a escalares en objetos JSON. Este formato especifica la variable/campo JSON y la ruta de acceso al elemento secundario, sin el simbolo de elemento raiz $.
   ![[Pasted image 20241213135001.png]]

3. Formato sintactico de azucar para matrices: El formato sugar XQL simplifica la referencia a un elemento de matriz determinado dentro de objetos JSON mediante corchetes y un indice numerico.
   **Matrices de referencia**: El formato sugar de XQL para hacer referencia a matrices en objetos JSON es jsonObj->jsonArrayPath[].
   ![[Pasted image 20241213135401.png]]

4. Formato de azucar sintactico para objetos JSON: El formato de azúcar XQL para hacer referencia a objetos JSON secundarios es jsonObj->jsonObjPath{}. Aquí, jsonObj es una variable o campo de tipo JSON, y jsonObjPath es la cadena de ruta de acceso a un elemento secundario sin $. Tenga en cuenta que los corchetes ({ }) al final de la cadena de ruta son necesarios para indicar que la ruta es de objeto (JSON).

	Ejemplos: En el ejemplo de la primera fila, la primera fase de modificación utiliza el formato sugar para asignar el objeto denominado B a una variable JSON denominada b1Obj. En el segundo paso, b1Obj se usa en otro formato de azúcar para acceder al escalar E. Tenga en cuenta que la misma tarea se puede lograr en una sola línea, como se muestra en la segunda fila.
	![[Pasted image 20241213135713.png]]
	
	