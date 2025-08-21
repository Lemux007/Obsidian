#Nodo

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
	
	