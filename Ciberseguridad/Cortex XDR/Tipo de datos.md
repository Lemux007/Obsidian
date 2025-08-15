# CAMPOS MULTIVALOR
1. ¿Qué son los campos multivalor (MVF) y por qué es tan importante su compatibilidad con los conjuntos de datos XSIAM? Los MVF son campos que pueden almacenar varios valores. Por ejemplo, considere una situación en la que desea almacenar las direcciones IP de los puntos de conexión en una tabla de base de datos. Un punto de conexión puede tener una o más direcciones IP porque cada tarjeta de red tiene una pila TCP/IP independiente.
   Tipos de diseño de campo:
   - Campos separados: Utilice un campo separado para cada direccion IP. Con esta opcion, no sabe el numero exacto de direcciones IP de antemano
   - Instrumentos de cuerda: Utilice una cadena que contenga todas las direcciones IP separadas por un delimitador.
   - Bases: Utilice BD que puedan tener campos multivalor.

	BD relacionales: No pueden tener campos multivalor, las celdas de la tabla que son campos son atomicas.
	BD no relacionales: BD que pueden tener campos multivalor.

2. Conjuntos de datos XSIAM: Los conjuntos de datos XSIAM contienen datos relacionados con la seguridad, como alertas y registros, a diferencia de los datos bien estructurados, como los datos sobre los libros de una biblioteca. Son BD no relacionales, que almacenan datos en formularios no tabulares. Por lo tanto un campo de un conjunto de datos puede contener varios valores y se conoce como campo multivalor.
3. Ejemplos de matrices JSON[], XQL puede direccionar valores individuales en un campo multivalor. El ejemplo que se muestra aqui es del conjunto de datos xdr_data, donde dns_resolutions es un tipo de campo de matriz JSON. La fase de modificacion asigna type1 al elemento type del segundo elemento de la matriz.
   ![[Pasted image 20241213162942.png]]
4. Esquemas de conjuntos de datos: Un esquema son datos sobre un conjunto de datos, que se almacenan en otro conjunto de datos. Un conjunto de datos esquema proporciona básicamente una descripción de todos los campos de un conjunto de datos determinado. Por lo tanto, cada conjunto de datos de XSIAM esta asociado a un conjunto de datos de esquema.
   - Tabla de esquemas: Podemos llamar al conjunto de datos de esquema una tabla de esquema porque no contiene ningun valor multivalor.
   - Pagina de busqueda: La pagina de busqueda XQL de la consola de administracion siempre esta asociada a un conjunto de datos. Si acaba de abrir la pagina de busqueda de XQL, el conjunto de datos asociado es el conjunto de datos predeterminado y la tabla esquema muestra la descripcion de este conjunto de datos predeterminado.
   - Campos: Un campo de los conjuntos de datos XSIAM puede almacenar uno o varios valores de los siguientes tipos: boolean, datetime, enum, float, int, json y string.

---
# TIPOS DE DATOS EN ASIGNACIONES DE FASES DE ALTERACION
1. Signo igual (=) en XQL: XQl utiliza el signo igual para la asignacion y la comparacion en las fases de modificiacion y filtro, respectivamente
   - Asignacion: alter variable = expresion
   - Comparasion: filter expresion1 = expresion2
     
    Variables frente a expresiones:
    - Variables: 
    - Expresiones: 
      ![[Pasted image 20241213164254.png]]

2. Asignacion en alter stage: la etapa de modificacion se utiliza para crear y actualizar variables y campos mediante la asignacion de nuevos valores o la modificacion de existentes
   - Alter: La etapa de modificacion crea o actualiza variables, como se muestra en el ejemplo de la priemra fila. Ademas se pueden combinar dos etapas de alteracion en una sola etapa.
     ![[Pasted image 20241213164631.png]]
     Tipos de datos admitidos: 
     ![[Pasted image 20241213164658.png]]
     
   - Campos y variables: son los mismos en XQL y estos dos terminos son intercambiables. Para crear un nuevo campo, puede especificar un nuevo nombre de variable en el lado izquierdo de una asignacion. 
---
# TIPOS DE DATOS EN LA ETAPA DE FILTRO
1. Tipos de datos en la etapa de filtro (comparacion): En la etapa de filtrado, el signo igual prueba la igualdad de los valores en sus lados izquierdo y derecho. Por lo tanto el signo igual en la fase de filtro es un operador booleano que devuelve verdadero o falso.
   Comparaciones de etapas de filtro: 
   ![[Pasted image 20241213170641.png]]
   ![[Pasted image 20241213170650.png]]
   
   Tipos de enumeracion: Puede usar el tipo de enumeracionen la etapa de filtro para las comparaciones. Sin embargo no se puede utilizar el tipo de enumeracion en la fase de modificacion para la asignacion. Por ejemplo, el campo event_tpe de xdr_data es de tipo enumeracion, lo que significa event_type de xdr_data