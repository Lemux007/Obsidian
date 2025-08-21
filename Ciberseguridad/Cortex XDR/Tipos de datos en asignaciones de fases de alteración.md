#Nodo

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