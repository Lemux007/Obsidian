#Nodo


![[Pasted image 20260112125653.png|900]]
Zona Untrust interface 1/1 192.168.78.253
Zona Trust interface 1/2 10.1.1.1/24
Zona DMZ interface 1/3 172.16.1.254/24
Interface administración 192.168.78.252

Dado el siguiente diagrama, realice los siguientes ejercicios:

a.  Configure las interfaces el FW en capa 3 y agrúpelas en tantas zonas de seguridad se indica.

b.  Asegúrese que las zonas Trust y DMZ tenga acceso a Internet.

c. Configure las reglas de seguridad necesarias para que la Zona Trust tenga acceso completo a la DMZ, pero de la DMZ solo se permitirá el PING y el RDP a la zona Trust

d. Los usuarios de la zona Trust tendrán negado el acceso a aplicaciones Peer to Peer, Facebook y youtube, excepto el usuario de la IP 10.1.1.15 el cual tendrá acceso a todo.

e. Configure la publicación de un servidor Web que vive en la zona DMZ y tiene la IP 172.16.1.15

# Creacion de Objetos




## a) Configurar interfaces en Capa 3 y crear zonas

### 1️⃣ Configurar interfaces Layer 3

**GUI → Network → Interfaces → Ethernet**

#### 🔹 ethernet1/1 (Untrust)

1. Click en **ethernet1/1**
    
2. Type: **Layer3**
    
3. Config:
    
    - IPv4: `192.168.78.253/24`
        
4. Virtual Router: **default**
    
5. Security Zone: _(la crearemos luego)_
    

👉 OK

---

#### 🔹 ethernet1/2 (Trust)

1. Click en **ethernet1/2**
    
2. Type: **Layer3**
    
3. IPv4: `10.1.1.1/24`
    
4. Virtual Router: **default**
    
5. Security Zone: _(pendiente)_
    

👉 OK

---

#### 🔹 ethernet1/3 (DMZ)

1. Click en **ethernet1/3**
    
2. Type: **Layer3**
    
3. IPv4: `172.16.1.254/24`
    
4. Virtual Router: **default**
    
5. Security Zone: _(pendiente)_
    

👉 OK

---

### 2️⃣ Crear Zonas de Seguridad

**GUI → Network → Zones → Add**

#### 🔹 Zona Untrust

- Name: `Untrust`
    
- Type: **Layer3**
    
- Interfaces: `ethernet1/1`
    

---

#### 🔹 Zona Trust

- Name: `Trust`
    
- Type: **Layer3**
    
- Interfaces: `ethernet1/2`
    

---

#### 🔹 Zona DMZ

- Name: `DMZ`
    
- Type: **Layer3**
    
- Interfaces: `ethernet1/3`
    

👉 Commit 🔄

---

## b) Asegurar acceso a Internet para Trust y DMZ

### 1️⃣ Ruta por defecto

**GUI → Network → Virtual Routers → default → Static Routes**

Add:

- Name: `Default-Route`
    
- Destination: `0.0.0.0/0`
    
- Next Hop: **IP Address**
    
- Next Hop IP: `192.168.78.1` _(gateway del ISP o router upstream)_
    

👉 OK

---

### 2️⃣ NAT de salida (Source NAT)

**GUI → Policies → NAT → Add**

#### 🔹 NAT Trust → Internet

- Name: `NAT_Trust_Internet`
    
- Source Zone: `Trust`
    
- Destination Zone: `Untrust`
    
- Source Address: `any`
    
- Destination Address: `any`
    
- Service: `any`
    

**Translated Packet**

- Source Translation: **Dynamic IP and Port**
    
- Interface Address: `ethernet1/1`
    

---

#### 🔹 NAT DMZ → Internet

- Name: `NAT_DMZ_Internet`
    
- Source Zone: `DMZ`
    
- Destination Zone: `Untrust`
    
- Source Address: `any`
    
- Destination Address: `any`
    
- Source Translation: **Dynamic IP and Port**
    
- Interface Address: `ethernet1/1`
    

👉 Commit 🔄

---

## c) Reglas entre Trust y DMZ

### 1️⃣ Trust → DMZ (acceso completo)

**GUI → Policies → Security → Add**

- Name: `Trust_to_DMZ_All`
    
- Source Zone: `Trust`
    
- Destination Zone: `DMZ`
    
- Source Address: `any`
    
- Destination Address: `any`
    
- Application: `any`
    
- Service: `any`
    
- Action: **Allow**
    

---

### 2️⃣ DMZ → Trust (solo PING y RDP)

**GUI → Policies → Security → Add**

- Name: `DMZ_to_Trust_Ping_RDP`
    
- Source Zone: `DMZ`
    
- Destination Zone: `Trust`
    
- Application:
    
    - `ping`
        
    - `ms-rdp`
        
- Service: `application-default`
    
- Action: **Allow**
    

---

### 3️⃣ Regla implícita de denegación

No necesitas crearla, PAN la trae por defecto 👍

👉 Commit 🔄

---

## d) Bloqueo de P2P, Facebook y YouTube (excepto 10.1.1.15)

### 1️⃣ Regla de EXCEPCIÓN (permitir todo a 10.1.1.15)

**Security Policy → Add (poner ARRIBA de todo)**

- Name: `Trust_10.1.1.15_Full_Access`
    
- Source Zone: `Trust`
    
- Source Address: `10.1.1.15`
    
- Destination Zone: `any`
    
- Application: `any`
    
- Service: `any`
    
- Action: **Allow**
    

---

### 2️⃣ Regla de BLOQUEO

**Security Policy → Add**

- Name: `Block_P2P_Facebook_Youtube`
    
- Source Zone: `Trust`
    
- Source Address: `any`
    
- Destination Zone: `Untrust`
    
- Application:
    
    - `facebook`
        
    - `youtube`
        
    - `bittorrent`
        
    - `edonkey`
        
    - `gnutella`
        
- Service: `application-default`
    
- Action: **Deny**
    

---

### 3️⃣ Regla de navegación general (opcional)

- Name: `Trust_to_Internet`
    
- Source Zone: `Trust`
    
- Destination Zone: `Untrust`
    
- Application: `any`
    
- Action: **Allow**
    

👉 Commit 🔄

---

## e) Publicación de servidor Web en DMZ (172.16.1.15)

### 1️⃣ NAT de destino (DNAT)

**GUI → Policies → NAT → Add**

- Name: `DNAT_Web_DMZ`
    
- Destination Zone: `Untrust`
    
- Destination Address: `192.168.78.253`
    
- Service: `service-http` _(o https)_
    

**Translated Packet**

- Destination Translation:
    
    - Address: `172.16.1.15`
        
    - Port: `80`
        

---

### 2️⃣ Regla de seguridad para el servidor Web

**Security Policy → Add**

- Name: `Allow_Web_DMZ`
    
- Source Zone: `Untrust`
    
- Destination Zone: `DMZ`
    
- Destination Address: `172.16.1.15`
    
- Application: `web-browsing`
    
- Service: `application-default`
    
- Action: **Allow**
    

 Commit 🔄