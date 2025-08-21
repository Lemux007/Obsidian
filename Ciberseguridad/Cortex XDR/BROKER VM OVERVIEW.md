#subindex 

- 
# INTRODUCCION A BROKER VM
1. Broker VM como canal de comunicaciones: Algunos puntos de conexión de la red interna utilizan agentes de Cortex XDR para comunicarse con Cortex XDR. Incluso cuando los dispositivos no ejecutan agentes, Broker VM proporciona un canal de comunicación alternativo y seguro para comunicar información relacionada con la seguridad a los servidores Cortex XDR.
   - Agentes: Cortex XDR se compone del trabajo combinado de Cortex XDR, que reside en Google Cloud Platform (GCP), y agentes y dispositivos de terceros que forman parte de su centro de datos, infraestructura híbrida o en la nube.
   - Sin agentes: Los sensores de terceros, como los servidores syslog y los firewalls que no son de Palo Alto Networks, necesitan un agente que reenvíe su información a Cortex XDR, y los usuarios necesitan un canal seguro a la nube para esta información en la que Cortex XDR confíe.

2. Maquina virtual de agente en Cortex XDR: Este diagrama muestra la funcion de Broker VM que conecta XDR y las redes internas con los usuarios.
   Se comunica entre sus redes y la funcionalidad de cortex XDR proporcionada en la nube.
   - Comunicacion segura
   - Redireccion de datos
   - Objetivos de datos
![[Pasted image 20241212102522.png]]
	Red interna del cliente: Puede contener puntos de conexion, servidores, dispositivos de terceros o centros de datos. agentes de Cortex XDR, firewalls de PAN, firewalls de terceros y otras fuentes de alertas y registros enrutan los datos a traves de Broker VM a Cortex XDR.

3. Broker VM como plataforma: Cortex XDR proporciona una funcionalidad que necesita información de sus dispositivos locales y sensores de seguridad. Por ejemplo, Cortex XDR proporciona a los analistas de seguridad una herramienta de análisis de causa raíz para identificar la causa raíz de un incidente. Esta herramienta, al igual que muchas otras, requiere información de dispositivos y sensores de seguridad (endpoints).
   - Reemplazo de varios agentes: En lugar de requerir que cada aplicación tenga su propio agente en los puntos finales de los usuarios, Broker VM es un agente unificado que recopila toda la información y la pone a disposición de Cortex XDR. Hay una máquina virtual de Broker instalada en las instalaciones del usuario, y cada servicio de Cortex XDR que necesita algo del entorno local tiene un applet de máquina virtual de agente que lleva la información a la máquina virtual de Broker, que a su vez informa de esta información a las aplicaciones basadas en la nube.
   - Prestacion de servicios de Cortex XDR: Los applets proporcionan servicios de Cortex XDR a los usuarios, y la máquina virtual de Broker ejecuta diferentes applets por separado en la máquina virtual mediante la autenticación del servidor de Cortex XDR. Diferentes applets sirven para diferentes propósitos. Actualmente, Broker VM admite los applets Configuración de agente local, Syslog Collector, Windows Event Collector, Network Mapper y Pathfinder.

--- 
[[Servicios y  applets de bróker VM]]
[[Bróker VM setup]]

