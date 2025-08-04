Es necesario contar con:
- memoria booteable con VMware ESXi
- ISO PAN_OS

1. Realizar arreglo RAID al servidor, se recomienda RAID 1 para la redundancia de los datos, posibles configuraciones:
	- F10 para intelligent provisioning
	- Navegar al storage advance settings
	
	Crear arreglo tipo RAID 1 usando los discos disponibles
	
2. Instalar VMware ESXi desde USB.
		1. Inserta la USB bootable con ESXi.
		2. Bootea desde la USB e instala ESXi en el volumen RAID.
		3. Define la contraseña de root y finaliza la instalación.
		4. Reinicia desde el disco (no desde USB).

3. Configuracion de Red.
	- IP Address: libre en la red (ej. ==192.168.120==.100)
	- Subnet Mask: 255.255.255.0
	- Gateway: ==192.168.120==.254 (gateway de la red)
	- DNS: 8.8.8.8 u otro local
	**La IP , el servidor y el pc deben pertenecer y estar conectados a la misma red, se recomienda uso del switch.**
Acc
