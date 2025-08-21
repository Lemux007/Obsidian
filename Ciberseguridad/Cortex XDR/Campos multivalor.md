#Nodo

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