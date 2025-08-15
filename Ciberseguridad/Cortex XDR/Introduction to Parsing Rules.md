# CONCEPTOS BASICOS DE LAS REGLAS DE ANALISIS
1. Informacion general sobre las reglas de analisis: El tema de las reglas de analisis no esta directamente en el dominio XQL. Sin embargo, debido a que su sintaxis se deriva de XQL. aqui ofrecemos una breve introduccion a las reglas de analisis.
   Definicion de reglas de analisis: Una regla de analisis analiza una entrada de registro sin procesar, aplica la logica de la regla a los campos de registro de entrada de analisis y a continuacion, prepara y devuelve una o varias filas para agregarlas a los conjuntos de datos. Dicha definicion dice que las reglas de analisis no estan en el dominio XQL; por ejemplo, no se puede utilizar una regla de analisis par consultar conjuntos de datos. En su lugar, las reglas de analisis son un componente del flujo de ingesta de datos XSIAM.
   
   Requisitos de la regla de analisis: Para trabajar con reglas de analisis en la consola de administracion de cortex XSIAM, un usuario necesita los niveles de autorizacion mas altos posibles; deben tener privilegios de administrador de cuentas o administrador de instancias de cortex XSIAM.
   
   **Proposito**: Eliminar las partes irrelevantes de los registros sin procesar entrantes. Es beneficioos organizar y limpiar los troncos antes de almacenarlos por dos razones:
   - Reduce los datos y ahorra espacio de almacenamiento
   - Mejora el rendimiento de las consultas XQL
     
    Tenga en cuenta que PAN generalmente sugiere usar reglas de nalisis para dos propositos especificos:
    - Agregar o normalizar marcas de tiempo cuando la fuente no las envia.
    - Eliminar los caracteres no validos de los registros

2. Sintaxis de las reglas de analisis: Aunque XSIAM tiene sus propias reglas de analisis unicas, su sintaxis comparte similitudes con XQL, ya que una parte de la sintaxis de la regla de analisis se deriva de XQL.
   **Secciones de reglas de analisis**: El subconjunto de XQL que se usa en las reglas de analisis se denomina XQLp, que significa XQL para analisis. Las fases de XQL que se pueden usar en las reglas de analisis son: **alter, fields, filter, join y call**
   Las reglas de analisis se organizan en torno a componentes de alto nivel denominados secciones. Estas secciones administran colectivamente como se analiza, procesa y se dirige a un conjunto de datos un registro sin procesar entrante. Estas secciones son: **INGEST, CONST, EXTEND Y RULE** Donde ingest es la unica obligatoria.
   
   Ej, en el ejemplo se muestra una regla de analisis con una seccion INGEST donde establece el conjunto de datos de destino en el que se almacenara finalmente el registro preprocesado. En este conjunto particular el conjunto de datos es pa_ed_raw, la regla de analisis se aplica a los registros del proveedor "pa" y del producto "ed".
   ![[Pasted image 20241216165152.png]]
   
3. Trabajar con reglas de analisis: Puede trabajar con reglas de analisis en la consola de administracion de cortex XSIAM. La pagina de reglas de analisis se encuentra en **Configuraciones > administracion de datos > menu reglas de analisis**.
   
   - Definido por el usuario: Las pestañas definido por el usuario muestra el editor de reglas para escribir sus propias reglas de analisis personalizadas que pueden anular las reglas predeterminadas.
   - Reglas predeterminadas: Muestran reglas de analisis proporcionadas por PAN. Tenga en cuenta que no puede editar estas reglas de analisis listas para usar; solo puedes verlos.
   - Ambas pestañas: Las pestañas ambas muestra el contenido de las dos primeras pestañas, reglas definidas por el usuario y reglas predeterminadas, una al lado de la otra.

4. Componentes del flujo de ingesta: Puede adjuntar varias instancias de Broker VM e instancias de XDR collector a la misma instancia XSIAM. Cada una de estas instancias puede recopilar registros de las aplicaciones que envian registros. Se requieren varias instancias del mismo tipo para equilibrar la carga y evitar tener un unico punto de error.
   
   En la imagen se muestra Broker VM, XDR collector y Cortex XSIAM, 3 componentes del flujo de ingesta, lo que hace estos componentes de flujo de ingesta sean relevantes es que son estos componentes los que realmente ejecutan las reglas de análisis.
   ![[Pasted image 20241216170349.png]]
   
   