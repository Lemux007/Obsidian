
1. Analisis del comportamiento: El motor de análisis de Cortex XDR detecta y responde a las amenazas ocultas posteriores a la intrusión que han evadido las defensas de la red antes de que los ataques arruinen los sistemas.
   
   Proceso para detectar anomalias:
   2. Aprender el comportamiento normal
   3. Comparar las actividades con el comportamiento normal

4. Tacticas de MITRE Att&ck: El motor de análisis puede generar una alerta para cualquiera de las siguientes tácticas de ataque, tal como se define en las tácticas de MITRE ATT&CK.
   - Execution: Las tácticas de ejecución incluyen varias técnicas para ejecutar código malicioso en un punto final local o remoto después de obtener acceso a la red.
   - Persistence: Las tácticas de persistencia son técnicas para mantener el acceso en una red o en un punto final.
   - Discovery: Las tácticas de descubrimiento son técnicas aplicadas después de un acceso inicial para identificar más vulnerabilidades dentro de la red.
   - Lateral movement: Las tácticas de movimiento lateral son técnicas para expandir la huella dentro de la red, incluida la obtención de credenciales para obtener acceso adicional a más datos en la red.
   - Comand and control: Las tácticas de comando y control (C2) permiten a los atacantes emitir comandos de forma remota a un endpoint y recibir información de él.
   - Exfiltration: Las tácticas de exfiltración son técnicas para recibir información, como datos empresariales valiosos, de una red.

3. Cobertura del motor de analisis: El motor de análisis Cortex XDR proporciona una cobertura completa de las tácticas de ataque detectadas según lo definido por las tácticas MITRE ATT&CK.
   - Descubrimiento: El motor detecta tácticas de detección a través de una búsqueda de síntomas en el tráfico de red interna, como cambios en los patrones de conectividad que incluyen mayores tasas de conexiones, conexiones fallidas y análisis de puertos.
   - Movimiento lateral: El motor detecta tácticas de movimiento lateral mediante el examen de operaciones administrativas, como Secure Shell (SSH), Protocolo de escritorio remoto (RDP) y Protocolo de transferencia de hipertexto (HTTP), acceso a recursos compartidos de archivos y uso de credenciales de usuario que va más allá de lo normal para su red.
   - Comando y control: Detecta tacticas de comando y control a traves de una busqueda de cambios inexplicables en la periodicidad de las conexeiones.
   - Exfiltracion: El motor detecta tácticas de exfiltración mediante el examen de las conexiones salientes con un enfoque en el volumen de datos que se transfieren.

4. Ejemplos de alertas de Analytics y fuentes de datos utilizadas: Los tipos de alerta que puede generar el motor de análisis de Cortex XDR dependen de las fuentes de datos (fuentes de registro) que configure.

5. Componentes basicos del motor de analisis: Detectores de analisis, El motor de análisis organiza sus actividades de análisis de comportamiento por unidades llamadas detectores. Cada detector está especializado para tipos de ataque específicos y genera un tipo de alerta analítica cuando se detectan anomalías y comportamientos sospechosos.

6. Habilitacion de Cortex XDR Analytics: **Configuracion > Configuraciones > Cortex XDR - Analisis**
   Los datos recopilados de al menos 30 puntos de conexion deben estar disponibles en el almacenamiento durante al menos dos semanas
   El motor requiere un minimo de 5 dias de recopilacion.

