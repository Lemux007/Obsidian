#Nodo

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
