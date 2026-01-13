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