#Nodo
1. Metodologia "shift-Right": La metodologia de desplazamiento a la derecha se centra aun mas en el ciclo de vida de un ataque, donde es mas escencial cazar. El atacante avanza de izquierda a derecha, comenzando con un reconocimiento general del entorno objetivo hasta la militarizacion y la entrega de malware, ya sea a traves de phishing u otros medios.
   
   - Reconocimiento, armamentizacion, entrega: Estas etapas del ataque implican
     - Acceso inicial, descubrimiento, evasion de la defensa, ejecucion
   - Explotacion, instalacion, mando y control, acciones sobre objetivos: Estas etapas del ataque implican
     - Escalada de privilegios, persistencia, mando y control, movimiento lateral, coleccion, acceso a credenciales, exfiltracion
       La caza de amenazas se realiza en estas etapas del ataque.

2. Ejemplo de reglas BIOC en cortex XDR: Varios BIOC vienen listos para usar con cortex XDR. Estos BIOC buscan tacticas, tecnicas y procedimientos especificos y cada uno de ellos se asigna a la categoria MITER ATT&CK o a la tactica MITER ATT&CK
   - Proceso de microsoft office que genera un proceso del que se abusa con frecuencia (Categoria: ejecucion)
   - Adobe Acrobat REader colocacion de un archivo ejecutable en el disco, categoria: cuentagotas
   - Proceso de windows enmascarado como un proceso sin firmar, categoria: evasion
   - El editor de ecuaciones de microsoft office genera un proceso del que se abusa con frecuencia, categoria: ejecucion
   - Archivo binario que se crea en un disco con una extension doble, categoria: ofuscacion de tipo de archivo
      
   - Proceso que intenta eliminar una herramienta de seguriad o antivirus conocida, categoria evasion
   - Powershell running with known mimikatz arguments, categoria coleccion
   - Proceso que se ejecuta desde la papelera de reciclaje, categoria evasion
   - Ejecutable creado en el disco por lsass.exe, categoria cuentagotas

3. Ejemplos de reglas BIOC en cortex XDR: IR a **Reglas > BIOC** para encontrar la pagina BIOC, esta pagina se enumeran todas las reglas BIOC integradas en el producto y que se pueden utilizar sin realizar cambios. puede editar o crear copias de estas firmas integradas mediante el generador de consultas y agregar sus propias exclusiones y ajustes
   
   Informacion sobre la consola de Cortex XDR
   - Name: nombre de BIOC
   - Tipo: Corresponde a la tactica o categoria MITRE ATT&CK a la que pertenece a la tecnica singular (Las de arriba, evasion, cuentagotas, etc)
   - Comportamiento: Es la firma que se creo
   - Severidad: Corresponde al riesgo de la tecnica. Si un ataque es de alta gravedad, es una tecnica de ataque es es muy arriesgada
   - Comentario: Descripcion de lo que es la tecnica del atacante

4. Caso practico: Busqueda de comportamientos de acceso a credenciales poco comunes mediante BIOC: En función de la metodología de desplazamiento a la derecha, debe centrarse en la búsqueda de la técnica de "volcado de memoria con comsvcs.dll", ya que es una técnica de acceso a credenciales. El acceso a credenciales como técnica es muy valioso para la búsqueda porque indica que un atacante puede haber progresado ya a través de los pasos para llegar a un punto de conexión y potencialmente ponerlo en peligro.
   
   - Comienzo: Busque comportamientos poco comunes de acceso a credenciales, como el acceso a credenciales sin usar herramientas como Mimikatz. Estas tecnicas son dificiles de detectar porque tienden a usar bibliotecas nativas del SO para volcar las credenciales de usuario
   - Formacion de casos de uso: Utilice BIOC incorporados, como el "volcado de memoria mediante comsvcs.dll" para buscar cualquier acierto
   - Recoleccion de herramientas: Utilice los cortex XDR BIOC como herramientas para esta busqueda.
   - Traduccion de casos de uso a firmas o analisis de datos: Segun el ciclo de vida de la busqueda de amenazas, traduzca los casos de uso a firmas en las herramientas.
   - Caza e investigacion: Por ultimo busca estas firmas especificas e investiga todo lo que encentres.