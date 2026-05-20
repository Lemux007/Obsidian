
(v1.0.0)

- [x] **Aislamiento de Namespace:** Creación del entorno dedicado `n8n`.
    
- [x] **Estabilización de Base de Datos:** Despliegue de PostgreSQL 15.
    
- [x] **Gestión de Credenciales:** Implementación de Kubernetes Secrets.
    
- [x] **Corrección de Base64:** Solución al error de "doble codificación" en los manifiestos.
    
- [x] **Optimización de Imagen:** Cambio de versiones experimentales a la versión estable **v2.20.7.
    
- [x] **Persistencia de Almacenamiento:** Implementación exitosa de `n8n-pvc-v5`.
    
- [x] **Base de Seguridad:** Implementación de llave de cifrado maestra **AES-256**.
    
- [x] **Control de Identidad:** Activación de User Management y creación de cuenta de Propietario.
    
- [x] **Gestión de Sesiones:** Restricción de duración de tokens JWT a 24 horas.
    

---

###  Hardening y Optimización (v1.1.0)


- [x] **Git hub repos:** Creacion de reporsitorios para configuracion y flujos   
    
- [ ] **Network Policies:** Aislar el pod de PostgreSQL para que solo acepte tráfico de n8n.
    
- [x] **Límites de Recursos:** Configurar topes de CPU y RAM en el YAML para evitar caídas del servidor.
    
- [ ] **Firewall del Host (UFW):** Restringir puertos en Ubuntu a solo el 22 y 30007.
    
- [ ] **HTTPS/TLS:** Migrar de NodePort a Ingress (Traefik) con certificados SSL.
    
- [ ] **Cabeceras de Seguridad:** Activar `N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS` y `N8N_BLOCK_XML_EXTERNAL_ENTITY`.
    
- [ ] **Automatización de Backups:** Scripts para exportar la base de datos a una ubicación externa.
    
- [ ] **Logs de Auditoría:** Activar el registro de auditoría de la API de Kubernetes.
    
- [ ] **Security Context:** Configurar el contenedor para que n8n no corra como usuario root.
    

