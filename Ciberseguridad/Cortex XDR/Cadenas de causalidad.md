
# CADENAS DE CAUSALIDAD
1. Region de ataque: Una región de ataque es un grupo de procesos en el árbol de procesos jerárquicos que están involucrados en un ataque. Uno de los desafíos que se presentan en este escenario es cómo distinguir qué procesos estuvieron involucrados en el ataque.

2. Instancias de causalidad: Las alertas vinculadas pueden revelar todos los procesos involucrados en actividades sospechosas. Una vez identificados los procesos responsables, sus operaciones sobre los recursos se pueden obtener fácilmente a partir de los datos mejorados del punto final
   ## Instancia de causalidad (CI)
   Cada grupo de procesos causalmente relacionados se denomina instancia de causalidad, o instancia de grupo de causalidad, Un objeto de instancia de causalidad puede incluir información sobre las interacciones proceso-recurso y las alertas, en función de la existencia de un ataque.
   ## Propietario del grupo de causalidad (CGO)
   En el caso de un ataque, el agente Cortex XDR termina todos los procesos en una instancia de causalidad, que se consideran responsables del ataque.

3. Formacion de instancias de causalidad: Cortex XDR proporciona una lista de procesos predefinidos y aprendidos conocidos como reproductores y desovadores finales. Ambos se actualizan a través de actualizaciones de contenido.
   - Desovadores: Para dividir el árbol de procesos en instancias de causalidad inconexas, el agente Cortex XDR utiliza procesos marcadores llamados generadores. Los procesos de generación son procesos especiales y aprendidos que el equipo de investigación identificó aprovechando las técnicas de aprendizaje automático (msiexec.exe, services.exe, winlogon.exe)
   - Generadores finales: Un solo ataque puede abarcar varias instancias de causalidad. Durante la investigación de amenazas, los generadores que pueden dar lugar a instancias de causalidad dependientes en un solo ataque también se identifican y agrupan bajo el nombre de generadores finales. (chrome.exe, firefox.exe, iexplore.exe)

[[Motor de análisis]]