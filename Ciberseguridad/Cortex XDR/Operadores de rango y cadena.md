#Nodo

1. Operadores de rango XQL: Los operadores de rango son utiles para filtrar y realizar operaciones condicionales para comprobar si un valor se encuentra dentro de un rango determinado. Porporcionan una forma concisa de especificar conjuntos de valores y realizar comprobaciones de pertenencia en las consultas XQL de cortex.
   ![[Pasted image 20241216105738.png]]
   
   - IN: Para utilizar el operador se debe especificar una lista de elementos separados por comas entre parentesis, por ejemplo (item 1, item 2, item3)
   - INCIDIR: Operador especial especifico para listas de direcciones IP, comprieba si existe una direccion ipv4 en la lista de direcciones proporcionada en la notacion de enrutamiento entre dominios sin clases.
   - OTHER RANGE OPERATORS:
     - not in: negacion booleana del operador in se utiliza para comprobar si un elemento no pertenece a una secuencia
     - incidr6, comprueba una direccion ipv6 en una lista con formato CIDR IPV6

2. Consulta de membresia XQL: Realice comprobaciones de pertenencia con XQL y determine si un valor coincide con alguno de los valores de un conjunto determinado.
   
   **IN**: En este ejemplo, la fase de filtro comprueba si el campo actor_process_image_name del registro es powershell.exe o wscript.exe mediante el operador "in".
   ![[Pasted image 20241216110450.png]]
   
   **NOT IN**; En este ejemplo, el operador "not in" devuelve true si el valor del campo event_type de un registro no está en la lista dada como operando derecho.
   ![[Pasted image 20241216110602.png]]
   
3. Consultar direcciones IP: Podemos utilizar el operador "incidr" para comparar una direccion ipv4 con un intervalo de direcciones IP en formato CIDR. El operador comprueba si la dirreccion IP se encuentra dentro del rango especificado por la notacion CIDR. 
   En este ejemplo, la etapa de filtrado selecciona solo los registros con action_remote_ip en el rango CIDR especificado 192.1.1.1/24 ![[Pasted image 20241216112133.png]]
   
   Ejemplo: En este ejemplo se muestra cómo comprobar el valor booleano devuelto por un operador XQL. Para lograr el resultado deseado, utilice la función if() en una etapa de alteración. La función if() evalúa una expresión booleana en su primer parámetro y devuelve el segundo o el tercer parámetro, dependiendo del valor booleano evaluado.
   ![[Pasted image 20241216112421.png]]
   
4. Operadores de cadena XQL: Facilitan la manipulacion y comparacion eficientes de los valores de cadena en las consultas, incluida la coincidencia de patrones y la extraccion de informacion. Ofrecen funcionalidad para la coincidencia de patrones, la coincidencia de expresiones regulares y otras operaciones para anlizar y extraer informacion. 
   ![[Pasted image 20241216113111.png]]
   - Contains not contains: devuelve true si su operando izquierdo contiene la subcadena dada con el operando derecho. Tambien puede buscar una subcadena en una lista de cadenas dada como una matriz de cadenas.
   - Operador "~=", tambien conocido como operador de coincidencia de expresiones regulares, comprueba si una cadena coincide con un patron dado como expresion regular. El operador devuelve true si su operando izquierdo coincide con el patron de expresiones regulares de su operando derecho, por ejemplo, name~=".*TestDog-*\.exe". (ojo con los asteriscos porque obsidian los toma como codigo para front)

4. Consultas XQL con operadores de cadena: Exploremos los operadores de cadena y algunos ejemplos de como usan XQL.
   - Cadena dentro de un registro: La fase de filtro utiliza el operador "contains" para seleccionar registro con un campo denominado "actor_process_image_name" que contiene la subcadena "psexec" ![[Pasted image 20241216113736.png]]
   - Cadena dentro de una matriz; En el conjunto de resultados, bool1 tendra el valor true porque la matriz contiene la subcadena "ef"
     ![[Pasted image 20241216113933.png]]
     
   - En este ejemplo la etapa de filtro selecciona los regitro con el campo action_process_image_name que coincide con el patron ".*Test(Dog|Gato).*\.exe"
     ![[Pasted image 20241216114312.png]]
     Logica de la consulta:
     - Cadena de longitud aleatoria: El patron espera que un nombre de archivo comience con una cadena de longitud aleatoria.
     - Cadena coincidente: Codificada con: ".*." A continuacion, espera ver "TESTDOG" o TESTCAT en* el nombre del archivo.
     - Permitir cadenas aleatorias: Se permite cualquier cadena aleatoria en el nombre del archivo
     - Calificar cadena con extension de archivo: El nombre del archivo debe terminar con ".exe"#Nodo
