# Funciones XQL:
1. Funciones XQL en consultas: Las funciones de XQL realizan acciones en sus argumentos y, como resultado, devuelven un valor. Proporcionan un nivel de abstracción para las personas que llaman, lo que simplifica las operaciones complejas. En los lenguajes de programación, las funciones pueden verse como una extensión de los operadores, que a su vez pueden considerarse como funciones especializadas. ![[Pasted image 20241213103238.png]]
   XQL Ejemplos de funciones
   - En este ejemplo, el comando alter stage se utiliza para realizar una asignación mediante las funciones integradas. La función current_time() devuelve la hora actual, y la función extract_time() se utiliza con el parámetro "DAY" para extraer el día del mes de la hora actual. El resultado se asigna al campo timeDay. ![[Pasted image 20241213103352.png]]
   - En este ejemplo, el comando alter stage se utiliza para realizar una asignación con las funciones integradas divide() y round(). La función divide() convierte el valor dataUp de bytes a kilobytes dividiéndolo por 1024, y la función round() se utiliza para redondear el resultado al número entero más cercano. Observe la apariencia de la variable dataUp en los lados izquierdo y derecho de la asignación.![[Pasted image 20241213103502.png]]
   - En este ejemplo, la etapa de filtro llama a la función len() para obtener la longitud de la variable de cadena.
     ![[Pasted image 20241213103611.png]]

2. XQL Functions Arguments: En XQL, los argumentos de función, también conocidos como parámetros, se especifican como una lista separada por comas entre paréntesis. Estos argumentos pueden ser obligatorios u opcionales, y algunas funciones pueden aceptar un número variable de argumentos. Cuando una función admite los tipos de argumentos obligatorios y opcionales, los argumentos necesarios deben colocarse antes de los opcionales.
   ![[Pasted image 20241213103944.png]]
   ![[Pasted image 20241213104124.png]]
   
# USO DE LA FUNCION XQL EN CONSULTAS
1. Funciones matematicas: Las funciones matematicas en XQL incluyen las funciones aritmeticas basicas; funciones de pavimento o redondeo, a la funcion de potencia; y funciones numericas enteras o de coma flotante.
   - Aritmetica basica: add(), divide(), multiply(), substract()
   - Floor(), devuelve un entero redondeado hacia abajo al numero entero mas cercano. Por ejemplo floor(3.6) devuelve el entero 3
   - Redondear, round() devuelve un numero entero redondeado al entero mas cercano, por ejemplo round(3.6) devuelve 4
   - Pow(x,y) devuelve x^y, es decir x a la potencia y
     
     Numero entero o de coma flotante: ![[Pasted image 20241213110418.png]]

2. Funciones de cadena: XQL proporciona muchas de las funciones de cadena que se encuentran en otros lenguajes de programacion, como la conversion de cadenas a minusculas y mayusculas, la concatenacion de dos cadenas y la division de cadenas en subcadenas. 
   
   - len() devuelve la longitud del argumento de cadena en un entero
   - string_count() devuelve un entero como el nunmero de apariciones de un patron en un argumento dado
   - split() devuelve una matriz de subcadenas
     Ejemplos: En este ejemplo, la función split() separa el valor de cadena "192.168.1.20" usando el separador "." y almacena las subcadenas encontradas en una matriz de cadenas. La fase de modificación agrega la variable ip_octets al conjunto de resultados.
     ![[Pasted image 20241213111344.png]]
     Una tabla de resultados no puede mostrar el contenido de la matriz a la vez
     ![[Pasted image 20241213111457.png]]
     
   - format_string() devuelve una cadena formateada a partir de argumentos de cadena mediante especificadores de formato

3. Funcion de conversion de tipos de datos: Las funciones y los operadores de los lenguajes de programación esperan tipos de datos correctos para sus argumentos. La mayoría de los lenguajes de scripting pueden convertir implícitamente tipos de datos, mientras que otros, como C/C++ y Java, requieren la conversión de tipos explicada. XQL proporciona funciones para conversiones de tipos. Algunos ejemplos son to_boolean(), to float() y to_string().
   ![[Pasted image 20241213111553.png]]
   
   Ejemplos: 
   ![[Pasted image 20241213112207.png]]
   ![[Pasted image 20241213112326.png]]
   ![[Pasted image 20241213112621.png]]
   
4. Funciones de procesamiento de matrices: Los conjuntos de datos XSIAM de Cortex no son bases de datos relacionales. Por lo tanto, los campos no son "atomicos" y pueden contener varios valores. Este tipo de campos tambien se denominan campos multivalor.
   ![[Pasted image 20241213112940.png]]
   ![[Pasted image 20241213113018.png]]
   
5. Arrayindex(): La función arrayindex() de XQL devuelve el valor almacenado en una ubicación de matriz específica especificada por el argumento index. En XQL, los índices de matriz comienzan con 0. Es decir, la primera ubicación es 0, la segunda es 1, y así sucesivamente. El tipo de retorno de arrayindex() es el tipo del valor almacenado.
   ![[Pasted image 20241213113213.png]]

6. Funciones de procesamiento JSON: JSON es importante en XQL pues proporciona sintaxis nativa, como la notacion de "azucar sintactico" y funciones especializadas.
   ![[Pasted image 20241213113422.png]]
   ![[Pasted image 20241213113651.png]]

7. Otras funciones de XQ: tambien proporciona una gama de funciones versatiles para diversos fines, incluida la manipulacion de datos relacionados con el tiempo, logica condicional y coincidencia de patrones.
   ![[Pasted image 20241213113825.png]]
   - El ejemplo muestra cómo calcular el día actual del mes. La etapa de modificación utiliza current_time() para devolver la marca de tiempo actual y, a continuación, extract_time() para extraer la parte DAY de la marca de tiempo actual. ![[Pasted image 20241213115151.png]]
   - En el ejemplo, la función if() toma tres argumentos; el primer argumento es una expresión booleana; El segundo y tercer argumento son valores de cadena. Si la expresión booleana se evalúa como true, se devuelve el segundo argumento ("first" en este ejemplo). De lo contrario, se devuelve el tercer argumento ("segundo" en el ejemplo).![[Pasted image 20241213115335.png]]
   - En este ejemplo, la función regextract() toma dos parámetros de cadena, val y exp. El parámetro exp, "a\db", especifica el patrón que se va a buscar: una "a" seguida de un dígito (\d) y, a continuación, una "b", como "a5b". La función identifica dos ocurrencias de este patrón en el parámetro val: "a4b" y "a5b".  El patrón "cualquier dígito" se representa normalmente mediante \d
     ![[Pasted image 20241213115620.png]]
 
