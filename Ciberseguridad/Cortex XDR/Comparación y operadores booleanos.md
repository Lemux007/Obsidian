#Nodo
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
   