# FUNDAMENTOS DE XQL
1. Componentes de las consultas XQL: XQL se utiliza para buscar registros en conjuntos de datos, la sintaxis se refiere a los elementos gramaticales o del lenguaje que componen una consulta XQL. Los elementos del lenguaje XQL incluyen etapas, funciones y operadores. 
   - Etapas: Las fases realizan determinadas operaciones en la evaluacion de consultas. Por ejemplo, la etapa del conjunto de datos especifica un conjunto de datos en el que se va a ejecutar la consulta. Las etapas mas utilizadas son el conjunto de datos, los campos, los filtros, la combinacion y la ordenacion. (conjunto de datos, campos, filtros, unir, ordenar)
   - Funciones: Algunas fases pueden llamar a funciones para convertir los datos a un formato deseado. Por ejemplo, current_time() devuelve la marca de tiempo actual mientras que extrac_time() puede obtener la informacion de la hora en la marca de tiempo. 
     | alter timepart = extract_time(current_time(), "HOUR")
   - Operadores: Los operadores en los lenguajes de programación son construcciones similares a funciones, pero difieren sintáctica y semánticamente. Por ejemplo, en general, puede escribir la suma de los números x e y usando una función de suma (x, y) o usando el operador x+y. Los operadores son tipos específicos de funciones para relacionar operandos.
   - | filter action_local_port in (1024,9999)
	
	![[Pasted image 20241212145835.png]]

2. Datasets: Las consultas XQL se ejecutan en conjuntos de dato, a los que se hace referencia como origenes de datos en XQL. Cada consulta opera en uno o varios conjuntos de datos. Es escencial que los conjuntos de datos de consulta ya existan durante la fase de diseño para garantizar la compilacion correcta de la consulta.
   - Conjunto de datos explicitos e implicitos: Los conjuntos de datos se pueden especificar de forma implicita o explicita en las consultas XQL. Para declarar explicitamente un conjunto de datos en una consulta, usaria la etapa del conjunto de datos, como se muestra ahora: 
     *Conjunto de datos = xdr_data* Si una consulta omite la fase del conjunto de datos, el compilador de consultas XQL no generara un error, en su lugar usara el conjunto de datos por predeterminado.
   - xdr_data: Disponible en todos los tipos de licencia de cortex XSIaM. puede cambiar el conjunto de datos predeterminado en **Configuraciones > administracion de conjunto de datos** desde la consola de administracion de Cortex XSIAM.

3. Saltos de linea en XQL: No hay ninguna restriccion en el numero de fases de una consulta XQL, lo que permie consultas potencialmente complejas. El compilador de consultas XQL omite los saltos de linea, lo que le permite dar formato a la consulta mediante saltos de linea para mejorar la legibilidad
   ![[Pasted image 20241212162238.png]]
   4. Comentarios en XQL Puede agregar comentarios en consultas XQL utilizando los mismos metodos que usaria en C/C++ y java. El compilador de consultas XQL omite los comentarios. Hay dos tipos de comentarios en XQL, en linea y bloque.
      - // Comentarios en linea
      - /* Comentarios en 
	        Bloque*/

   5. Indistincion entre mayuscula y minuscula en XQL: Algunos lenguajes de programacion como C, java, python y JS distinguen entre mayusculas y minusculas, mientras que SQL y XQL no lo son.
      

# ENTORNO DE DESARROLLO DE XQL
1. Pagina de busqueda de XQL: La pagina de busqueda de XQL en la consola de administracion de Cortex XSIAM proporciona todos los elementos escenciales para cread, editar, compilar, ejecutar y ver resultados. En esta leccion, esta pagina se denomina entorno de desarrollo XSIAM
   
   Acceso al entorno de desarrollo de XQL:
   - Desde el generador de consultas
   - Desde el centro de consultas
   - Navegador
   - Quick Launcher

2. Editor de consultas: El editor de consultas XSIAM muestra el 
   - nombre de la consulta, 
   - las entradas de codigos de color, 
   - resalta los errores de sintaxis y 
   - proporciona opciones de finalizacion automatica.

3. Opciones para ejecutar consultas: Puede ejecutar la consulta en primer plano o en segundo plano, tambien se puede guardar o programar.
4. Resultados de la consulta: Los resultados de la consulta muestran los resultados de la busqueda en un formato tabular de forma predeterminada, conocido como tabla de resultados. Tambien pueden mostrar los resultados en otros graficos.
   