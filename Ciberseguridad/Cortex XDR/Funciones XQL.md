#Nodo

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