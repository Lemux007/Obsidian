
## 1. VirusTotal (Ciberseguridad)


- **Costo Enterprise:** Generalmente entre **$20,000 y $50,000 USD anuales** (modelo basado en cuotas de API y asientos).
    
- **Modelo Free:** 4 solicitudes por minuto; 500 solicitudes al día.
    
- **Limitaciones Free:** No permite escaneo privado (tus archivos se comparten con la comunidad), límites de API muy estrictos para flujos de alto volumen en n8n.
    
- **Ventaja Enterprise:** **Privacidad total** (los archivos no se comparten), acceso a _Retrohunt_ y cuotas masivas de API para procesar miles de archivos automáticamente en n8n sin bloqueos.
    

## 2. Notion (Gestión de Proyectos/Wiki)


- **Costo Enterprise:** Aproximadamente **$20 - $25 USD por usuario/mes** (contrato anual).
    
- **Modelo Free:** Bloques ilimitados para individuos, hasta 10 invitados.
    
- **Limitaciones Free:** No tiene SAML SSO, el historial de versiones es de solo 7 días y la API tiene límites de frecuencia (throttling) más agresivos.
    
- **Ventaja Enterprise:** **Seguridad avanzada (SSO)**, historial de páginas ilimitado, y registros de auditoría. En n8n, esto te permite crear dashboards corporativos robustos con sincronización de bases de datos de gran tamaño sin preocuparte por la retención de datos.
    

## 3. WhatsApp Business API (Comunicación)

El canal de salida para notificaciones críticas o bots de atención al cliente.

- **Costo Enterprise (Platform):** Se paga por **conversación de 24 horas**. Los precios varían por país (ej. México/EE. UU. ~$0.01 - $0.04 USD por conversación de utilidad/marketing).
    
- **Modelo Free:** La "WhatsApp Business App" es gratis. La API tiene un **tier gratuito de 1,000 conversaciones** de servicio al mes.
    
- **Limitaciones Free:** La App manual no se puede integrar nativamente con n8n de forma escalable (requiere emuladores o servicios externos). La API requiere un BSP (Business Solution Provider).
    
- **Ventaja Enterprise:** Integración oficial vía **Webhooks** en n8n. Permite enviar mensajes masivos autorizados, usar plantillas interactivas y manejar múltiples agentes simultáneamente.
    

## 4. GitHub (Repositorio y CI/CD)


- **Costo Enterprise:** **$21 USD por usuario/mes**. Si añades Copilot Enterprise, suma **$39 USD**.
    
- **Modelo Free:** Repositorios públicos/privados ilimitados con 2,000 minutos de GitHub Actions.
    
- **Limitaciones Free:** Menos minutos de computación para CI/CD y falta de controles de seguridad avanzados como el escaneo de secretos (vital para que tus llaves de API de n8n no se filtren).
    
- **Ventaja Enterprise:** **Advanced Security** (detecta llaves API en tu código), entornos de despliegue protegidos y mayor almacenamiento en LFS para activos pesados que n8n pueda procesar.
    

## 5. Claude (IA Generativa)


- **Costo Enterprise:** Precio personalizado (estimado en **$60 USD por usuario/mes**, mínimo de asientos usualmente 70+).
    
- **Modelo Free:** Acceso limitado a Claude 3.5 Sonnet con cuotas que se agotan rápido.
    
- **Limitaciones Free:** No tiene ventana de contexto expandida, sin garantías de privacidad de datos para entrenamiento y límites de mensajes muy bajos para un bot que reciba mucho tráfico.
    
- **Ventaja Enterprise:** **Ventana de contexto masiva** (puedes enviarle manuales enteros vía n8n), prioridad en tiempos de respuesta y cumplimiento de seguridad (tus datos no entrenan sus modelos), lo cual es crítico si procesas info sensible de clientes.
