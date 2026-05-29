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

%%
## Drawing
```compressed-json
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
```
%%