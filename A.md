### 1. "Cuéntame sobre ti"

> _"Soy Ingeniero en Computación egresado del IPN. A lo largo de mi experiencia me he enfocado en resolver problemas operativos y de negocio utilizando tecnología: desde el desarrollo con **Python y consumo de APIs REST**, hasta la automatización de flujos con herramientas como **n8n y Power Automate**._
> 
> _Lo que más disfruto es tomar un proceso manual, desarmar el problema, entender qué necesita el usuario final y construir una solución que funcione sola y sin fricción. Me considero alguien con mucha iniciativa: me siento cómodo cuando el requerimiento no está perfectamente definido, investigo la documentación, pruebo y entrego resultados. Por eso me llamó tanto la atención Nortrez y su enfoque en implementar soluciones sobre monday.com y plataformas low-code."_

### 2. "Háblame de tu experiencia en Stellantis" (Tu carta fuerte para este rol)

> _"En Stellantis estuve muy cerca de la operación diaria. Mi rol principal consistió en **levantar procesos con usuarios y áreas operativas** que hacían muchas tareas manuales en hojas de cálculo y correos._
> 
> _Utilicé **Power Automate y Power Apps** para crear flujos automatizados y herramientas internas que eliminaron cuellos de botella. Lo más valioso ahí no fue solo la herramienta, sino aprender a escuchar al usuario, entender qué le dolía de su proceso y traducirlo a una lógica estructurada de pasos, condiciones y notificaciones sin que nadie me estuviera dictando el 'cómo' paso a paso."_

### 3. "Háblame de NOVA"

> _"En NOVA trabajé en la orquestación y automatización de procesos técnicos. Utilicé **n8n conectado mediante APIs REST y Webhooks** para manipular cargas de datos en formato JSON entre diferentes plataformas y bases de datos._
> 
> _También desarrollé lógica en **Python** para automatizar el procesamiento de alertas y tareas repetitivas, empaquetando servicios en contenedores **Docker** bajo entornos Linux. Esto me dio una base muy sólida para entender cómo viajan los datos entre aplicaciones y cómo manejar errores cuando un endpoint falla."_

### 4. "Háblame de Prestanómico"

> _"Prestanómico fue un entorno Fintech muy dinámico donde apoyé en la validación e integración de sistemas. Trabajé consumiendo y revisando **APIs REST** con Postman, validando respuestas, autenticación por tokens y consistencia de datos en bases de datos relacionales como **PostgreSQL**._
> 
> _Además, generé scripts en **Python y Bash** para automatizar tareas rutinarias de validación y respaldos, asegurando que la información entre los servicios fuera confiable y estructurada."_

### 5. "Fortalezas y Debilidades"

**Fortalezas:**

- **Tolerancia a la ambigüedad y autonomía:** _"No me paralizo si un cliente o líder me da una idea vaga. Me gusta investigar la API, leer la documentación técnica, mapear el flujo y presentar una propuesta funcional."_
    
- **Capacidad de traducción técnica-negocio:** _"Puedo hablar con código y estructuras de datos, pero también sé sentarme con una persona no técnica y explicarle el flujo en términos sencillos y prácticos."_
    

**Debilidad (bien orientada):**

- _"A veces me clavo mucho en querer optimizar cada detalle del código o del flujo desde el inicio para que sea perfecto. He aprendido a modular eso priorizando primero la entrega de un Producto Mínimo Viable (MVP) que resuelva el dolor inmediato del usuario, y luego iterar mejoras."_
    

### 6. Expectativa Salarial

> _"Revisando el esquema publicado de la vacante ($11,000 a $16,000 brutos), mi expectativa se ubica en el tope de **$16,000 brutos mensuales**._
> 
> _Considero que encaja bien porque no llego en blanco: ya tengo experiencia construyendo flujos con n8n y Power Automate, domino Python, consumo de APIs y levantamiento de requerimientos con usuarios. Mi curva de aprendizaje con monday.com y las herramientas del equipo va a ser inmediata."_


### 1. "¿Cómo le explicarías qué es una API o un Webhook a un cliente que no sabe nada de tecnología?"

Buscan ver si puedes hablar sin tecnicismos frente a directores o gerentes.

- **Tu respuesta:**
    
    > _"Le pondría la analogía de un restaurante: una **API** es como el mesero. Tú (el usuario en monday.com) no entras a la cocina a preparar la comida; le dices al mesero qué quieres, él va al sistema del restaurante (el servidor externo), toma la orden y te trae el platillo listo. Y un **Webhook** es como una notificación automática: en lugar de que estés preguntándole al mesero a cada minuto '¿ya está mi comida?', la cocina te avisa en el instante exacto en que el platillo salió para que hagas lo que sigue."_
    

### 2. "Si una automatización falla a mitad de camino y no sabes por qué, ¿cuál es tu proceso para resolverlo?"

Quieren ver si entras en pánico o si tienes método de depuración (_troubleshooting_).

- **Tu respuesta:**
    
    > _"Primero reviso los **logs de ejecución** y el código de error HTTP (un 400 por payload mal formado, un 401 por token vencido o un 500 por caída del servicio). Luego aíslo el paso exacto donde se rompió: tomo el JSON que generó la falla y hago pruebas directas en Postman o en el nodo de prueba para replicarlo. Una vez identificado el problema, aplico el ajuste, manejo la excepción para que el flujo no muera silenciosamente si vuelve a ocurrir, y notifico al equipo si hay algún retraso en la sincronización."_
    

### 3. "Cuéntame de alguna ocasión donde te dieron una tarea súper ambigua y cómo la resolviste"

Esta pregunta valida directamente el filtro que pusieron en la vacante.

- **Tu respuesta (apóyate en Stellantis):**
    
    > _"En Stellantis, un área operativa se acercó diciendo simplemente: 'perdemos mucho tiempo con los reportes diarios y queremos automatizarlo', sin ningún detalle técnico ni requerimiento formal. Lo que hice fue sentarme con ellos a ver cómo trabajaban durante una hora: identifiqué de dónde sacaban los datos (hojas de Excel dispersas y correos), hacia dónde debían ir y qué reglas lógicas aplicaban. Dibujé un diagrama de flujo simple, se los mostré para validar que ese fuera el proceso real y construí un primer prototipo funcional en Power Automate. Les ahorró horas de trabajo y transformó una queja vaga en un flujo automatizado y documentado."_
    

### 4. "¿Qué harías si un cliente te pide una integración o automatización que técnicamente no es posible o la plataforma no soporta?"

Buscan evaluar tu asertividad y manejo de frustración con usuarios.

- **Tu respuesta:**
    
    > _"Nunca le digo un 'no se puede' seco al cliente. Primero entiendo cuál es el **objetivo de negocio** detrás de lo que me está pidiendo: muchas veces piden una solución específica porque creen que es la única forma, pero lo que necesitan es el resultado. Si la herramienta no tiene un conector nativo, evalúo alternativas: consumir la API directa mediante un script intermedio o diseñar un flujo en dos fases. Si de plano hay una limitante técnica insalvable, se lo explico de forma transparente con los motivos claros y le presento dos caminos viables para lograr un resultado equivalente."_
    

### 5. "¿Qué tanto conoces monday.com o plataformas similares?"

Sé honesto sin restarte valor.

- **Tu respuesta:**
    
    > _"Conozco bien la arquitectura de monday.com a nivel de tableros, columnas de estado y sus capacidades nativas de automatización. Mi mayor experiencia práctica ha sido con plataformas middleware como **n8n y Power Automate**, integrando APIs REST y Webhooks. Como la lógica de disparadores (_triggers_), condiciones y acciones es fundamentalmente la misma, mi curva para dominar el ecosistema profundo de monday.com es cuestión de días."_