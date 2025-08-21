#Nodo

IE Zero Day CVE-2013-3893: Operation Deputy Dog, campaña de ataque utilizada para atacar a objetivoos japoneses, usaba una vulnerabilidad de internet explorer al acceder a un objeto en la memoria que ha sido eliminado, permitiendo ejecutar codigo en una maquina con solo visitar un web malicioso.

Adobe Reader CVE-2013-3346: Turla / Snake / Uroburos, campaña de ciberespionaje en curso. Se uso correos de spear phishing que utilizan una vulnerabilidad de adobe reader.

Adobe Flash CVE-2015-3010/0311: Dirigida a servicios financieros y de defensa de EU.

El objetivo de cualquier exploit es llegar al kernel del sistema operativo para ejecutar operaciones de privilegios como llamadas al sistema o API.


TECNICAS DE EXPLOTACION Y MECANISMOS DE DEFENSA
	Componentes principales: HW, SO y Procesos.
1. Segmentación del espacio de direcciones virtuales de un proceso
	- Mensaje de texto: Instrucciones
	- Datos: Variables globales y estaticas
	- Monton (Heap): Asignaciones de memoria dinamica en tiempos de ejecucion.
	- Pila (Stack): Usada para almacenar los datos dependientes de la funcion.
	  ![[Pasted image 20250113124336.png|400]]

2. Metodo de ataque por desbordamiento de bufer: Basado en la falta de comprobacion de la longitud de los valores de entrada, si los datos criticos siguen inmediatamente a la ubicacion de la memoria el atacante puede afectar al flujo general del programa.
   
   El atacante agrega mas informacion de la esperada, en x86 se procesa el valor inmediatamente despues de que el bufer de entrada almacena con frecuencia la ubicacion de la siguiente instruccion de lenguaje maquina que va a ejecutar.
    ![[Pasted image 20241204130642.png]]
   Como PROTEGERSE? Con STACK CANARIES
   Asignamos un valor fijo en la memoria justo antes del puntero de ejecucion. Este valor se denomina canario de pila por llevar a un canario a minas para detectar modificaciones. Cualquier cambio en la pila mandara un exception.
   
   NOP SLED para mejorar ataques
   Los atacantes utilizan la técnica de trineo NOP para mejorar los ataques de desbordamiento de búfer
   Los ataques de desbordamiento de búfer se basan en la capacidad del atacante para colocar shellcode en ubicaciones de memoria conocidas, lo que puede ser difícil de lograr para el atacante. Los atacantes utilizan la técnica del "trineo NOP" para tratar de superar este obstáculo
   NOP es la representacion en lenguaje ensamblador de una instruccion en lenguaje maquina que no realiza ninguna operacion. Un trineo NOP es una secuencia de estos NOP
   
   
   Prevencion de ejecucuion de datos (DEP)
   Ayuda a protegerse contra vulnerabilidades de seguridad al impedir que la CPU ejecute codigo de las paginas de memoria a menos que esten marcadas como ejecutables.

3. Metodo de ataque de programacion orientada al retorno (ROP)
   Usado para un uso ilegitimo de funciones y rutinas de bibliotecas legitimas, no es codigo creado, es codigo reutilizado tomado y recibe un retorno a una llamada de funcion.
    ![[Pasted image 20241204132058.png]]