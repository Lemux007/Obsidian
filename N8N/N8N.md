---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Build ^3jlnKnuT

-Version: Ubuntu server 24
-Computer name: nvappsrvn8n
-Database: PostgreSQL
    ¬ Persistency: local-path
-Infra: k3s via Rancher
-namespace: n8n
-Active pods:
    ¬ App pod: n8n
    ¬Database pod: postgres
-deploy: YAML Manifest (Kubectl) ^Vb4MzO9E

SSL/TLS Certificate ^G4KWecAX

openssl req -x509 -nodes -days 180 -newkey rsa:2048 \
-keyout n8n.key \
-out n8n.crt \
-subj "/CN=n8n.local" \
-addext "subjectAltName=DNS:n8n.local"

kubectl create secret tls n8n-tls \
--key n8n.key \
--cert n8n.crt \
-n n8n ^bNxSUdAX

Commands ^cYa9qO0R

kubectl rollout restart deployment n8n -n n8n
sudo kubectl get pods --all-namespaces | grep n8n ^uxOKu1WM

Restart service ^hbrtpvzB

Set up ^UDwgYKUI

1.Preparar Servidor (Ubuntu) ^Bt0X5usM

Update server ^apUrjkOx

sudo apt update && sudo apt upgrade -y ^0yTTFrkP

Basic dependecies ^UIXWlgFo

sudo apt install -y curl apt-transport-https ca-certificates gnupg ^Rqeth5rA

2.Kubernetes install ^CTi4Q0na

curl -sfL https://get.k3s.io | sh - ^zpGn3aNv

Verify ^UHZLuGFH

sudo kubectl get nodes ^IHYn97Fc

3. Configure kubectl (normal user) ^SiexxXnT

mkdir -p $HOME/.kube
sudo cp /etc/rancher/k3s/k3s.yaml $HOME/.kube/config
sudo chown $USER:$USER $HOME/.kube/config ^K5wa3euM

4. Create namespace for N8N ^4WnZDFcC

kubectl create namespace n8n ^mFgBExRh

5. Data Base (PostgreSQL) ^g85X1Gsb

nano postgres.yaml ^6u8WB2vx

Code of the file: ^bK6kxX2Q

apiVersion: v1
kind: Secret
metadata:
  name: postgres-secret
  namespace: n8n
type: Opaque
data:
  POSTGRES_DB: bjhu
  POSTGRES_USER: bjhu
  POSTGRES_PASSWORD: bjhuM3Bhc3M=

---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: postgres-pvc-v4
  namespace: n8n
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: postgres
  namespace: n8n
spec:
  replicas: 1
  selector:
    matchLabels:
      app: postgres
  template:
    metadata:
      labels:
        app: postgres
    spec:
      containers:
        - name: postgres
          image: postgres:15
          ports:
            - containerPort: 5432
          envFrom:
            - secretRef:
                name: postgres-secret
          volumeMounts:
            - name: postgres-storage
              mountPath: /var/lib/postgresql/data
      volumes:
        - name: postgres-storage
          persistentVolumeClaim:
            claimName: postgres-pvc-v4
---
apiVersion: v1
kind: Service
metadata:
  name: postgres
  namespace: n8n
spec:
  selector:
    app: postgres
  ports:
    - port: 5432
      targetPort: 5432

 ^qMXzl6ha

Apply changes ^CfPOR6s1

kubectl apply -f postgres.yaml ^CYw8PNwK

Verify ^oneftRg0

kubectl get pods -n n8n
kubectl get pvc -n n8n
kubectl get svc -n n8n ^3oI1lrMw

Expected output ^gPhUzYZz

- Pod en Running
- PVC en Bound
- Service activo ^UJGUYuPG

- Pod en Running
- PVC en Bound
- Service activo ^B3yqysk7

- Pod en Running
- PVC en Bound
- Service activo ^k5BR6Xj6

- Pod en Running
- PVC en Bound
- Service activo ^AxSGyIIG

- Pod en Running
- PVC en Bound
- Service activo ^cBewMUt6

Persistency validation ^vZannGDo

kubectl delete pod -n n8n -l app=postgres ^wK5eUKjb

kubectl get pods -n n8n ^uT2u3OyE

No lose of data when running  = all correct ^OoduihA0

6. Deployment of N8N ^IeO0kgnS

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: n8n-pvc-v4
  namespace: n8n
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: n8n
  namespace: n8n
spec:
  replicas: 1
  selector:
    matchLabels:
      app: n8n
  template:
    metadata:
      labels:
        app: n8n
    spec:
      containers:
        - name: n8n
          image: n8nio/n8n:2.20.7
          ports:
            - containerPort: 5678
          env:
            - name: DB_TYPE
              value: postgresdb
            - name: DB_POSTGRESDB_HOST
              value: postgres
            - name: DB_POSTGRESDB_PORT
              value: "5432"
            - name: DB_POSTGRESDB_DATABASE
              value: n8n
            - name: DB_POSTGRESDB_USER
              value: n8n
            - name: DB_POSTGRESDB_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: postgres-secret
                  key: POSTGRES_PASSWORD
          volumeMounts:
            - mountPath: /home/node/.n8n
              name: n8n-storage
      volumes:
        - name: n8n-storage
          persistentVolumeClaim:
            claimName: n8n-pvc-v4
---
apiVersion: v1
kind: Service
metadata:
  name: n8n-service
  namespace: n8n
spec:
  type: NodePort
  selector:
    app: n8n
  ports:
    - port: 5678
      targetPort: 5678
      nodePort: 30007

 ^SPOpsPFv

n8n.yaml ^RVw9rYFO

Apply ^6Oi4VqJl

kubectl apply -f n8n.yaml ^ry8aZwJo

Apply ^g35wSu1R

7.Access ^xPmpvH8g

http://IP_DEL_SERVIDOR:30007 ^sfUZ5Rmq

In this config there was a change of url with the host files ^0XZJolsc

Set up Desktop
 ^9accpc4e

1. sudo apt update && sudo apt upgrade -y
2. sudo apt install -y curl wget git build-essential
3. sudo apt install -y net-tools
4. TEST: node -v
5. curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
6. export NVM_DIR="$HOME/.nvm"
        source "$NVM_DIR/nvm.sh"
7. TEST:nvm --version
8. npm install -g n8n
9. n8n -v
10. n8n
11. http://localhost:5678


FIX LOAD:
1. export NVM_DIR="$HOME/.nvm"
        [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
2. nvm --version
3. Reinstall: nvm install --lts
                                nvm use --lts
4. node -v
        npm -v        
        
                
5. npm install -g n8n
 ^vCCXw5X6

Monitoreo ^b7qLYPp1

- paessler: Monitoreo de la infraestructura
- Notion ^yg0snra3

- Filtro por estatus de cerradas o abiertas
- Refinamiento de promp para que no una todas las alertas como un solo evento si no separadas  ^vVaShF38

Conexiones ^2bbhHlrX

Operaciones ^0uJPTQBc

- Documentación.
- Generacion de procesos.
- Wiki, bases de conocimiento(conectar memorias de Agents).
- Memorias Tecnicas.
- Respaldos.
- Creacion de Tareas y reuniones.
- Desarrollo de Capital Humano
- Reduccion de tiempo de respuesta de tickets y/o alertas de seguridad 
- Medir KPI y ROI 
- BPA's
- Autorizacion de acciones con ventanas o notificaciones dinamicas(boton de aceptar-negar)
- Generacion de dashboards de resultados, ejecuciones de workflows ^yEIJCRbf

Gestion de tickets ^E6gHXSjy

- Trend Micro
- Tanium
- PAN
- Qualys ^b19nVELT

- Teams
- Outlook
- Whatsapp ^Wk9H6Laq

Flujos de autorización: Cuando intervendra el usuario o cuando
se le notificara ^MhzmWcRy

MSSP,s: ^NxsJOO8h

Medio de alerta ^nnbwJFjT

Metricas clave ^X4JFctyw

- Horas ahorradas 
- Tiempo de Respuesta
- % Automatizacion vs manual ^EBJKS0MG

Gestion de alertas ^N5vgtbL5

Proactivanet ^rNdtMMJL

Agentes AI ^4kovYSsj

SMTP ^1pHmiJMr

Host: novasistemas.relay.tmes.trendmicro.com
Port: 25
Client Host Name: nvappsrvn8n.novasistemas.com.mx ^Rm5jSIAj

Logs ^Z3PZZfpH

sudo kubectl logs -f deployment/n8n -n n8n ^wBYpdCpf

Image Version ^RRiQa1Jj

sudo kubectl get pod -n n8n -o 
jsonpath='{.items[0].spec.containers[0].image}' ^sbfM9tma

Verificar Volumenes (PVC) ^MjBzDEi2

sudo kubectl get pvc -n n8 ^d1z5AYmc

Verificar estado de Pods ^MxUmndTm

sudo kubectl get pods -n n8n ^COErwEzN

Storage ^jXhdwVvq

Local Path Provisioner

    - Postgres PVC(postgres-pvc): 5Gi volumen "bound"
    - n8n PVC: /home/node/.n8n  ^U6NhzPI2

Enviroment variables ^cGbw8Zte

N8N_ENCRYPTION_KEY ^Q5YaLqXe

const apiResponse = $input.first().json;

const alerts = apiResponse.alerts || apiResponse.data || apiResponse.items || [];

const resumen = alerts.map((alert, i) => ({
  index: i + 1,
  id: alert.id || alert.alertId || 'N/A',
  severidad: alert.severity || alert.riskLevel || 'desconocida',
  tipo: alert.type || alert.alertType || alert.category || 'N/A',
  descripcion: alert.description || alert.message || alert.name || 'Sin descripción',
  host: alert.host || alert.deviceName || alert.endpoint || 'N/A',
  ip: alert.ip || alert.sourceIp || alert.targetIp || 'N/A',
  fecha: alert.createdAt || alert.timestamp || alert.detectionTime || new Date().toISOString(),
  estado: alert.status || 'new',
  malware: alert.malwareName || alert.threatName || null,
  accion: alert.action || alert.dispositionAction || 'pendiente',
  usuario: alert.userName || alert.user || null,
  cve: alert.cve || alert.vulnerabilityId || null
}));

const stats = {
  total: resumen.length,
  criticas: resumen.filter(a => ['critical','high','critica','alta'].includes((a.severidad || '').toLowerCase())).length,
  medias: resumen.filter(a => ['medium','media'].includes((a.severidad || '').toLowerCase())).length,
  bajas: resumen.filter(a => ['low','baja','info'].includes((a.severidad || '').toLowerCase())).length
};

return [{
  json: {
    alertas: resumen,
    estadisticas: stats,
    timestamp: new Date().toISOString(),
    rawTotal: apiResponse.totalCount || resumen.length,
    prompt: `Eres un experto en ciberseguridad especializado en Trend Micro. Analiza estas alertas y responde SOLO con un JSON válido sin backticks ni texto adicional:\n\nALERTAS:\n${JSON.stringify(resumen, null, 2)}\n\nESTADÍSTICAS: total=${stats.total}, críticas=${stats.criticas}, medias=${stats.medias}, bajas=${stats.bajas}\n\nResponde ÚNICAMENTE con este JSON:\n{\n  "veredicto_global": "CRÍTICO|ALTO|MEDIO|BAJO|LIMPIO",\n  "nivel_riesgo_numerico": <1-10>,\n  "resumen_ejecutivo": "<2-3 oraciones>",\n  "amenazas_principales": [{"amenaza": "", "impacto": "", "urgencia": "INMEDIATA|ALTA|MEDIA|BAJA"}],\n  "activos_comprometidos": ["<host o IP>"],\n  "recomendaciones": ["<acción 1>", "<acción 2>", "<acción 3>"],\n  "requiere_intervencion_inmediata": <true|false>,\n  "tiempo_respuesta_sugerido": "<inmediato|1 hora|4 horas|24 horas|72 horas>",\n  "contexto_tecnico": "<análisis técnico detallado>"\n}`
  }
}]; ^6UsE28mX

Apagar servicios ^ruQuXvG7

Prender servicios ^13C36iz6

sudo systemctl stop k3s ^e4XeNxYH

sudo systemctl start k3s ^eKUyRZ3m

Verify Healt ^4DhXUg2R

kubectl get all -n n8n ^BqA7pntI

kubectl describe pod (pod) -n n8n ^qtOJfIfI

Start PVC ^YLftx9gI

sudo kubectl apply -f postgres.yaml
sudo kubectl apply -f n8n.yaml ^zi9i9BVD

intervals of 15s between lines ^DyMTusm1

Logs ^LahlbGv8

sudo kubectl logs (pod) -n n8n ^9nq6Q5nD

Watch real time status ^6CnUCRkQ

sudo kubectl get pods -n n8n -w

sudo kubectl logs -l app=n8n -n n8n -f
 ^jP3dagUL

sudo kubectl get pods -n n8n -w ^bzkwwK7s

## Embedded Files
56412801dd8f722a5363ebeb09b4811b37c09057: [[8242c32f-931d-4789-9ca1-9d80c1067aef.png]]

%%
## Drawing
```compressed-json
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
```
%%