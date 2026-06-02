

### Base del Despliegue (v1.0.0)

- [ ] **Aislamiento de Namespace:** Creación y delimitación del entorno lógico dedicado `namespace: n8n` para separar la aplicación de otros servicios del sistema.
    
- [ ] **Estabilización de Base de Datos:** Despliegue e inicialización de PostgreSQL 15 como motor de persistencia centralizado.
    
- [ ] **Gestión de Credenciales:** Implementación de _Kubernetes Secrets_ nativos para el manejo seguro de contraseñas de la base de datos y llaves de licenciamiento.
    
- [ ] **Corrección de Base64:** Solución técnica al error de doble codificación que corrompía los secretos en los manifiestos YAML iniciales.
    
- [ ] **Optimización de Imagen:** Migración estratégica de versiones de desarrollo inestables a la versión oficial y testeada de producción **v2.20.12** (actualizada desde la v2.20.7 original).
    
- [ ] **Persistencia de Almacenamiento:** Configuración exitosa del _PersistentVolumeClaim_ (`n8n-pvc-v5`) asignando 10GiB estables para evitar pérdida de datos ante reinicios de Pods.
    
- [ ] **Base de Seguridad:** Generación y despliegue de la llave de cifrado maestra AES-256 (`N8N_ENCRYPTION_KEY`) para proteger los datos en reposo dentro de la base de datos.
    
- [ ] **Control de Identidad:** Activación del módulo de _User Management_ con la asignación del rol primario de Propietario de la instancia.
    
- [ ] **Gestión de Sesiones:** Endurecimiento del ciclo de vida de las sesiones restringiendo los tokens JWT a una duración máxima estricta de 24 horas.
    

### Hardening y Optimización de Infraestructura (v1.1.0)

- [ ] **Estrategia GitOps & Código:** Creación y separación de repositorios en GitHub; uso de la rama `main` para el respaldo completo de la Infraestructura como Código (IaC) y una rama/esquema independiente para la lógica de los _workflows_.
    
- [ ] **Respaldos Automáticos de Arquitectura:** Clonación y sincronización de las políticas de auditoría del sistema y configuraciones centrales de K3s directamente en la carpeta local `k3s-cluster-config/` empujada al repositorio privado.
    
- [ ] **Network Policies (Aislamiento Total):** Implementación de reglas de red de confianza cero a nivel de orquestador para aislar el Pod de PostgreSQL, bloqueando cualquier intento de conexión que no provenga explícitamente del Pod de n8n.
    
- [ ] **Límites Estrictos de Recursos:** Configuración de topes de cómputo en el manifiesto de Kubernetes fijados en **3 Cores de CPU y 6GB de Memoria RAM** para mitigar ataques de denegación de servicio (DoS) por consumo de memoria.
    
- [ ] **Firewall del Host (UFW):** Cierre perimetral del servidor Ubuntu. Se bloquearon del exterior los puertos críticos `30007` (NodePort), `5432` (Postgres local) y `6443` (API Server de K3s), permitiendo únicamente los puertos seguros `22` (SSH) y `80/443` (Tráfico Web).
    
- [ ] **HTTPS/TLS Avanzado:** Eliminación del acceso inseguro vía NodePort mediante la implementación de un _Ingress Controller_ de Traefik para enrutar el tráfico bajo certificados cifrados SSL/TLS hacia `[https://n8n.local](https://n8n.local)`.
    
- [ ] **Cabeceras de Seguridad de Aplicación:** Inyección de variables nativas en el Pod para mitigar ataques de Inyección de Entidades Externas XML (`N8N_BLOCK_XML_EXTERNAL_ENTITY=true`) y bloqueo de alteración de archivos de configuración (`N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true`).
    
- [ ] **CronJob de Backups Nativo:** Programación de un recurso de automatización efímero dentro del clúster que se ejecuta diariamente a las 00:00 (Medianoche). Este genera un volcado en caliente (`pg_dump`), lo comprime en formato `.sql.gz` y lo guarda mediante un volumen `hostPath` en la ruta persistente del servidor `~/n8n-backups/`.
    
- [ ] **Logs de Auditoría de Kubernetes:** Activación del motor de auditoría interna de la API de Kubernetes mediante una política personalizada (`audit-policy.yaml`). El clúster ahora escribe un registro JSON inmutable en `/var/log/k3s-audit.log` con rotación automatizada a los 100MB y retención de 30 días.
    
- [ ] **Security Context (Ejecución No-Root):** Reconfiguración del manifiesto de despliegue para prohibir la ejecución del contenedor como usuario administrador del sistema, forzando al orquestador a correr n8n bajo el usuario sin privilegios `node` (UID 1000).


| **Vulnerabilidad Detectada**           | **Riesgo Original**                                                                                                    | **Solución Técnica Implementada**                                                                                           |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Ejecución como Usuario Root**        | Elevado: Si el contenedor de n8n era vulnerado, el atacante ganaba control total del nodo de Ubuntu.                   | **Security Context:** Se forzó la ejecución del Pod bajo el usuario no-root UID 1000.                                       |
| **Inyección de Código XML (XXE)**      | Medio-Alto: Vulnerabilidad en librerías que permitía lectura de archivos del sistema mediante payloads XML maliciosos. | **Hardening de Configuración:** Activación de la bandera restrictiva `N8N_BLOCK_XML_EXTERNAL_ENTITY`.                       |
| **Movimiento Lateral en la Red**       | Elevado: Si un Pod secundario o comprometido entraba al clúster, podía extraer la base de datos de n8n directamente.   | **Network Policies:** Bloqueo absoluto de tráfico hacia el puerto 5432 de Postgres, permitiendo únicamente al Pod de n8n.   |
| **Intercepción de Tráfico (Sniffing)** | Alto: Las credenciales y contraseñas viajaban en texto plano a través del puerto expuesto por NodePort.                | **Traefik Ingress + TLS:** Cifrado completo del canal de comunicación mediante HTTPS nativo.                                |
| **Exposición Perimetral de APIs**      | Alto: El puerto de control de Kubernetes (6443) y la DB (5432) respondían a escaneos de internet.                      | **Firewalling (UFW):** Filtrado estricto en el Host de Ubuntu; accesos directos externos completamente eliminados (_DROP_). |
| **Falta de Trazabilidad e Impunidad**  | Medio: Modificaciones maliciosas de recursos de la infraestructura pasaban desapercibidas sin dejar huella.            | **K3s API Auditing:** Creación del archivo de auditoría inmutable en tiempo real `/var/log/k3s-audit.log`.                  |
| **Pérdida de Datos o Ransomware**      | Alto: Fallos en el disco o corrupción del contenedor borraban permanentemente los flujos y credenciales de clientes.   | **CronJob Automated Backup:** Respaldo local diario, en caliente y automatizado de PostgreSQL.                              |

