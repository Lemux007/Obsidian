1. Software instalado (Vulnerabilidades, EOL y componentes de IA)
    

Con **Trend Vision One (ASRM / Executive Dashboard / Vulnerability Management)** o **Apex One (Vulnerability Protection / Application Control)**, pueden obtener el inventario completo de software en sus endpoints.

La solución detecta vulnerabilidades conocidas (CVEs), software obsoleto o en Fin de Vida Útil (EOL).

En cuanto a **extensiones de navegador y herramientas de IA**, la telemetría del agente de Trend detecta aplicaciones instaladas, ejecutables no autorizados y plugins/extensiones de riesgo mediante el módulo de visibilidad de activos (**Asset Discovery / Risk Insights**).

2. Carpetas compartidas e identificación de sus atributos
    

Limitado.

Trend es una solución de EDR/XDR y protección de endpoints, no un software de inventario de activos de TI (ITAM) o auditoría de servidores de archivos.

Pueden detectar si hay puertos o servicios de compartición de archivos expuestos (como SMBv1 o recursos compartidos abiertos con riesgos de propagación de malware). Sin embargo, no genera un reporte nativo en forma de lista tabulada con todas las carpetas compartidas locales y sus permisos ACL.

3. Usuarios locales y sus atributos
    

Parcial / Enfoque en Riesgo.

Mediante **Identity Risk Insights / Asset Visibility** en Vision One, Trend les permite identificar cuentas de usuario activas, cuentas con privilegios elevados (**Administradores Locales**) y comportamientos anómalos de identidad.

Si lo que buscan es identificar usuarios locales con permisos excesivos (un riesgo clave para el gobierno de IA), Trend lo cubre perfectamente. Si requieren un volcado masivo y plano de cada usuario local creado en el sistema operativo (incluso los inactivos a nivel de registro SAM), esa es una función nativa de Microsoft Active Directory / Intune.

4. Nivel de hardening (Evaluación basada en CIS Benchmark)
    

**Trend Vision One ASRM** cuenta con una evaluación de **Device Posture (Postura de Seguridad del Dispositivo)** que mide configuraciones de riesgo, falta de parches, controles desactivados y brechas de seguridad del sistema operativo.

Si utilizan **Trend Cloud One - Conformity** (para servidores/nube), la evaluación contra marcos **CIS Benchmarks** es 100% nativa e integrada.

Para endpoints tradicionales, la consola les genera índices de riesgo (**Risk Score**) y recomendaciones de hardening alineadas a estándares como CIS y NIST.

Para cubrir al 100% el volcado masivo de usuarios locales (registro SAM) y la auditoría detallada de carpetas compartidas con permisos ACL, se pueden integrar las siguientes tecnologías:

- **Qualys :**
    
    - **Carpetas y ACLs:** A través de sus módulos **Qualys Policy Compliance (PC)** y **CyberSecurity Asset Management (CSAM)**, permite auditar configuraciones a nivel del sistema operativo. Mediante controles personalizados (Custom Controls), Qualys puede extraer la lista exacta de recursos compartidos locales (`SMB/NetShare`) junto con sus permisos de acceso (ACLs).
        
    - **Usuarios locales:** Extrae el inventario completo de la base de datos SAM (incluyendo usuarios inactivos o deshabilitados) como parte de sus auditorías de cumplimiento.