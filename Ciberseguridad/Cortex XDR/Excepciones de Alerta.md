#Nodo

1. Creacion de excepciones de alerta: Clico del boton secundario en una alerta > crear excepcion de alerta
   La creacion de excepciones de alerta solo esta disponible para algunos tipos de alerta, por ejemplo wildfire no puede.
   ![[Pasted image 20250110174807.png|400]]
2. Tipos de excepcion: La tabla de alertas muestra el nombre de la alerta, el tipo de excepcion que se realizara. **Endpoints > Policy Management > Profiles**.
   Visualizacion de las excepciones de su perfil: Se crean dos tipos de excepciones al realizar crear excepcion de alerta en las alertas respectivas: Excepcion de regla BTP y excepcion de firma digital, estos tipos de excepcion solo se pueden crear desde el menu contextual de alertas.

3. Alerta excepcion frente a alerta de exclusion: Puede distinguir entre una excepción de alerta y una alerta de exclusión. Los resultados de realizar las acciones de excepción de alerta y exclusión de alerta son los mismos**.** No verá ninguna alerta de este tipo en la tabla Alertas de la consola de administración.
   
   Las *excepciones* de alerta son *implementadas por el agente de Cortex XDR*. Al realizar esta acción en una alerta, Cortex XDR envía un comando al agente para que ya *no genere ninguna alerta de este tipo*.
   Sin embargo, el agente de Cortex XDR no tiene nada que ver con las *exclusiones de alertas.* El agente *sigue creando y enviando alertas* de este tipo, pero Cortex XDR las *ignora como alertas.*
   ![[Pasted image 20250110175348.png|400]]