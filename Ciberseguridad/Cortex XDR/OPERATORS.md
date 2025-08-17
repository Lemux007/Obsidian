# COMPARACION Y OPERADORES BOOLEANOS
1. Descripcion general de los operadores XQL: Los operadores son construcciones similares a funciones en los lenguajes de programación. Al igual que las funciones, los operadores toman argumentos conocidos como operandos, les aplican una acción y, a continuación, devuelven el resultado de la accion al autor de la llamada. Los operandos XQL constan de variables (campos) y valores XQL
   **Metodos de codificacion con operadores**: Los operadores XQL estan presentes en los lenguajes de programacion para proporcionar un estilo de codificacion mas natural e intuitivo para la sintaxis. 
   
   - Concatenacion con una funcion: str3 = concat(str1, str2)
   - Concatenacion con un operador: str3 = str1 + str2
     
    Categorizacion de operadores, XQL organiza los operadores en diferentes grupos, lo que facilita a los usuarios trabajar con varios tipos de operaciones y condiciones en sus consultas. 
    - Comparacion: Comparan valores y determinan su relacion. Evaluan si dos valores son iguales, no iguales, mayores que, menores que, mayores o iguales a que, o menores o iguales entre si.
    - Booleano, realizan operaciones logicas y combinan condiciones, en XQL los operadores AND logico y OR logico.
    - Rango: Los operadores de rango (pertenencia) se utilizan para determinar si un valor es miembro de un rango o conjunto especifico. (in o not in)
    - String: Los operadores de cadena se utilizan para manipular y comparar cadenas. (Contains, Not contains).

2. Operadores de comparacion XQL: XQL proporciona operadores de comparacion basicos, tambien conocidos como operadores relacionales, como igual =, menor que < y menor o igual que <=.
   ![[Pasted image 20241216100530.png]]
   
   Operador de igualdad: Se sobrecarga en funcion de cada etapa:
   - Alter: En alter el igual funciona como un operador de asignacion
   - Filter: El igual funciona como un operador de comparacion que devuelve verdadero o falso
     
3. Operadores booleanos XQL: XQL admite los operadores booleanos (logicos) basico y/o que combinan dos o mas expresiones booleanas en etapas de filtro Por ejemplo: ![[Pasted image 20241216101219.png]]
   Completo:
   ![[Pasted image 20241216101233.png]]
   
---
# OPERADORES DE RANGO Y CADENA
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
     - Calificar cadena con extension de archivo: El nombre del archivo debe terminar con ".exe"