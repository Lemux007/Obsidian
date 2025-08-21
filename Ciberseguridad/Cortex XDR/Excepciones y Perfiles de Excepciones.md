#Nodo
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