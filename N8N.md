- Version: Ubuntu 25.10 amd64
- Version: Ubuntu server 24  

- User: novaman
- Password: novaAu0mation1

- Computer name: nvappsrvn8n

N8N Local:

shorta@novasistemas.com.mx
N0v4n8nauto!!

openssl req -x509 -nodes -days 180 -newkey rsa:2048 \
-keyout n8n.key \
-out n8n.crt \
-subj "/CN=n8n.local" \
-addext "subjectAltName=DNS:n8n.local"

kubectl create secret tls n8n-tls \
--key n8n.key \
--cert n8n.crt \
-n n8n

# SET UP Ubuntu server:

# 1. Preparar el servidor (Ubuntu)

Actualizar el sistema:

```bash
sudo apt update && sudo apt upgrade -y
```

Instalar dependencias básicas:

```bash
sudo apt install -y curl apt-transport-https ca-certificates gnupg
```

---

# 2. Instalar Kubernetes 


```bash
curl -sfL https://get.k3s.io | sh -
```

Verificar:

```bash
sudo kubectl get nodes
```

---

# 3. Configurar kubectl (usuario normal)

```bash
mkdir -p $HOME/.kube
sudo cp /etc/rancher/k3s/k3s.yaml $HOME/.kube/config
sudo chown $USER:$USER $HOME/.kube/config
```

---

# 4. Crear namespace para n8n

```bash
kubectl create namespace n8n
```

---

# 5. Base de datos (PostgreSQL)


```
nano postgres.yaml
```

```
apiVersion: v1
kind: Secret
metadata:
  name: postgres-secret
  namespace: n8n
type: Opaque
data:
  POSTGRES_DB: bjhuOA==        # n8n (base64)
  POSTGRES_USER: bjhuOA==      # n8n (base64)
  POSTGRES_PASSWORD: bjhuM3Bhc3M=  # n8n3pass (base64)

---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: postgres-pvc
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
        - mountPath: /var/lib/postgresql/data
          name: postgres-storage
      volumes:
      - name: postgres-storage
        persistentVolumeClaim:
          claimName: postgres-pvc

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
```


Aplicar:

```bash
kubectl apply -f postgres.yaml
```

Validacion:

```
kubectl get pods -n n8n
kubectl get pvc -n n8n
kubectl get svc -n n8n
```

- Pod en **Running**
- PVC en **Bound**
- Service activo
Validar Persistencia

```
kubectl delete pod -n n8n -l app=postgres
```

```
kubectl get pods -n n8n
```

levanta sin perder datos → todo correcto

---

# 6. Deployment de n8n

```yaml
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
        image: n8nio/n8n
        ports:
        - containerPort: 5678
        env:
        - name: DB_TYPE
          value: postgresdb
        - name: DB_POSTGRESDB_HOST
          value: postgres
        - name: DB_POSTGRESDB_DATABASE
          value: n8n
        - name: DB_POSTGRESDB_USER
          value: n8n
        - name: DB_POSTGRESDB_PASSWORD
          value: n8npass
        - name: N8N_BASIC_AUTH_ACTIVE
          value: "true"
        - name: N8N_BASIC_AUTH_USER
          value: admin
        - name: N8N_BASIC_AUTH_PASSWORD
          value: admin123
```

---

# 7. Exponer el servicio

```yaml
apiVersion: v1
kind: Service
metadata:
  name: n8n-service
  namespace: n8n
spec:
  type: NodePort
  ports:
    - port: 5678
      targetPort: 5678
      nodePort: 30007
  selector:
    app: n8n
```

```bash
kubectl apply -f n8n.yaml
```

Acceso:

```
http://IP_DEL_SERVIDOR:30007
```

---

# SET UP Desktop:

```
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


´´