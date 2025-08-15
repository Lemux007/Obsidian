1. Configurar de expceciones: Para ver las reglas de excepción nuevas y existentes, vaya a **Configuración > Configuración de excepciones**. En la página Configuración de excepciones, hay cuatro submenús: Exclusiones de alertas, Reglas de supresión de IOC/BIOC, Deshabilitar reglas de prevención y Excepción heredada.
2. Reglas de exclusion de alertas: Una regla de exclusión de alertas es una regla para suprimir alertas de Cortex XDR.
   Podemos crear exclusiones de alertas en la consola de administracion haciendo clic en ** Manage alert > Excluir alerta**
   ![[Pasted image 20250110174143.png]]
3. Incidentes y alertas excluidas: El estado de un incidente se ve afectado por la exclusión de las alertas asociadas a ese incidente, Si se excluye el 100 por ciento de las alertas restantes de un incidente, el estado del incidente cambiará automáticamente a "Resuelto – Resolución automática".
4. Accion de alerta de exclusion frente a creacion de una regla de exclusion: 
   - Se mostrará una regla de exclusión en la tabla Exclusiones de alertas que se encuentra en **Configuración > Configuraciones de excepciones > Exclusiones de alertas**. Por el contrario, una acción de exclusión de alerta individual (excluir una alerta individual mediante un clic derecho) no se mostrará en la tabla Exclusiones de alertas.
   - Al dejar de poner en cuarentena un archivo, se excluyen las alertas relacionadas mediante la creacion de una regla de exclusion en lugar de una exlusion de alerta individual


# EXCEPCIONES Y PERFILES DE EXCEPCIONES
1. Excepciones de alerta frente a exclusiones de alerta: *Una exclusion silencia alertas para que no aparezcan en la consola de Cortex XDR, una excepcion deshabilita por completo la proteccion, una exclusion de alerta es diferente a una excepcion de alerta.*
2. Perfiles de excepciones: Puede crear excepciones en perfiles de excepcion. Una excepcion en la consola de administracion de Cortex XDR es una configuracion de desactivacion de proteccion. Puede ajustar eficazmente la configuración de seguridad mediante excepciones que anulen la configuración de seguridad aplicada en los puntos de conexión
3. Tipos de excepcion: 
   - Excepcion de *proceso*: Deshabilita los modulos de proteccion contra malware y exploits seleccionados en un proceso para permitir que se ejecute un archivo
   - Excepcion de *soporte*: Para abordar temporalmente los problemas de politica de un cliente especifico
   - Excepcion a la regla de proteccion contra amenazas conductuales: (*BTP*) deshabilita una regla BTP especifica para permitir que un proceso siga ejecutandose
   - Excepcion de *reglas de analisis local*: Deshabilita todas las reglas de analisis local implicadas en la creacion de una alerta especifica
   - Excepcion de *analisis avanzado*: Basado en la nube, puede crear una excepcion de analisis avanzado despues del analisis de un archivo de volcado de memoria
   - Excepcion de *firmante digital*: Quita un firmante que no es de confianza de la lista de bloqueo para permitir que los archivos firmados por este firmante se ejecutan
   - Excepcion del *motor de inspeccion de paquetes de red*: deshabilita una regla de inspeccion de paquetes de red que esta implicada en la creacion de una alerta especifica.

4. Analisis avanzado: El análisis avanzado es un análisis automático de volcados de memoria en la nube. En el análisis avanzado, las instancias de Cortex XDR recuperan volcados automáticamente, cargan volcados en un servicio de análisis de volcados basado en la nube para un análisis avanzado y recopilan veredictos del servicio de análisis.
   *Volcados de memoria o memory dump*: Archivos de registro que almacenan el contenido que tenia la memoria del sistema en un momento dado. 
   Flujo de prevencion de exploits: 
   ![[Pasted image 20241210151013.png]]
   Configuracion de analisis avanzado:
   Configuracion > configuraciones > configuracion general > agente LA configuracion general permite que una instancia de XDR se conecte al servicio de analisis de volcado basado en la nube.


# EXCEPCIONES DE ALERTA
1. Creacion de excepciones de alerta: Clico del boton secundario en una alerta > crear excepcion de alerta
   La creacion de excepciones de alerta solo esta disponible para algunos tipos de alerta, por ejemplo wildfire no puede.
   ![[Pasted image 20250110174807.png|400]]
1. Tipos de excepcion: La tabla de alertas muestra el nombre de la alerta, el tipo de excepcion que se realizara. **Endpoints > Policy Management > Profiles**.
   Visualizacion de las excepciones de su perfil: Se crean dos tipos de excepciones al realizar crear excepcion de alerta en las alertas respectivas: Excepcion de regla BTP y excepcion de firma digital, estos tipos de excepcion solo se pueden crear desde el menu contextual de alertas.

3. Alerta excepcion frente a alerta de exclusion: Puede distinguir entre una excepción de alerta y una alerta de exclusión. Los resultados de realizar las acciones de excepción de alerta y exclusión de alerta son los mismos**.** No verá ninguna alerta de este tipo en la tabla Alertas de la consola de administración.
   
   Las *excepciones* de alerta son *implementadas por el agente de Cortex XDR*. Al realizar esta acción en una alerta, Cortex XDR envía un comando al agente para que ya *no genere ninguna alerta de este tipo*.
   Sin embargo, el agente de Cortex XDR no tiene nada que ver con las *exclusiones de alertas.* El agente *sigue creando y enviando alertas* de este tipo, pero Cortex XDR las *ignora como alertas.*
   ![[Pasted image 20250110175348.png|400]]
# EXCEPCIONES GLOBALES
1. Aplicaciones de excepciones globales: Las excepciones globales se aplican incondicionalmente a todos los puntos de conexión. Como alternativa, puede navegar a **Endpoints > Policy Management > Profiles > Exceptions Profiles** y aplicar excepciones a endpoints específicos mediante reglas de política. Las excepciones en ambos ámbitos agregan todas las excepciones aplicadas.
   - Las excepciones en los perfiles de execepciones se aplican a los puntos de conexion determinados por las directivas
   - Las excepciones globales se aplican a todos los puntos de conexion sin necesidad de reglas de directiva
   - Las excepciones globales junto con las excepciones de los perfiles, constituyen la suma de todas las excepciones que se aplican a los extremos.
   - Ajusta globalmente algunas opciones de configuracion en otros perfiles.

	Creacion de excepciones globales: Para crear una excepción global, vaya a **Administración de políticas > Prevención > Excepciones globales**. Esto se utiliza para las excepciones de proceso y soporte.
	
