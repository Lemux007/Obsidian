#Nodo

INSTANCIA DE CORTEX XDR (Entorno dedicado a cortex)
	En general se crea una instancia de cortex xdr por inquilino o cliente, que puede ser una organizacion, empresa o equipo. por ejemplo una isntancia de cortex xdr se crea en google cloud plattform a traves de la activacion de instancias
		Activacion de instancia y del inquilino hace referencia a la misma tarea
1. Una instancia: Practica comun crear dos o mas instancia para separar los entornos de prueba y produccion.
2. Activacion de instancias: Requiere de una licencia en forma de numero de serie, es una tarea unica que tarda hasta una hora, en la activacion se crean instancias de componentes de SW y se extienden en GoogleCP.
3. Interacciones: Usuarios de cortex XDR pueden interactuar con sus instancias mediante la consola de administracion de Cortex XDR, la API de cortex XDR e integraciones externas.

4. Consola de administracion Cortex XDR: se usa para interactuar con la instancia. los usuarios tipicos son operadores SOC, analistas de soc e ingenieros de seguridad.
	1. Investigar: Incidentes y alertas y responder a amenazas
	2. Gestionar: Seguridad en los edp a traves de politicas y perfiles
	4. Crear: actualizar agentes o crear paquetes de instalacion
	5. Ver: paneles y generar informes
	   
	   
5. Administracion de A2: autenticacion y autorizacion necesarias para interactuar con las instancias de cortex XDR. Por ejemplo, para acceder a la instancia de administracion de Cortex XDR.
	1. Aplicaciones en la nube: Portal de atencion al cliente, puerta de enlace cortex XDR, inicio de sesion unico.
	   
6. Portal de atencion al cliente: Los clientes de PAN pueden acceder al portal de soporte para realizar las tareas relacionadas con el producto, como crear un caso de soporte, registrar un dispositivo, administrar otros activos como licencias, descargar SW etc.
   
7. Puerta de enlace Cortex XDR: Usada para administrar instancias, incluida la activacion de nuevas, visualizacion y el acceso a instancias a utorizadas.
8. Inicio de sesion unico: El inicio de sesión único (SSO) proporciona un método de autenticación coherente para todas las aplicaciones en la nube, CSP, la puerta de enlace Cortex XDR y la consola de administración Cortex XDR de una instancia.

  

La autenticación de dos factores se puede configurar por usuario de CSP. La autorización se gestiona a través del control de acceso basado en roles (RBAC) para los usuarios de CSP y los scripts externos mediante la API de Cortex XDR. En el caso de los scripts externos, la autenticación se proporciona mediante la generación de claves.


TRABAJAR CON UN AGENTE DE CORTEX XDR
1. Plataformas de SO compatibles: Hay versiones del SO de cortex XDR en windows, mac, linux, anroid y ios, pero android no proporciona proteccion contra vulnerabilidades de seguridad.
	1. Virtual desktop: XDR se puede instalar en los edp de la VDI (Infraestructura de escritorio virtual). 
	2. Linux containerized: Sistema predominante para las aplicaciones que se ejecutan en nubes publicas.
	3. Kubernetes Support: Cortex XDR Cloud per Host es companible con kubernetes
	   
2. Agente de CORTEX XDR para hosts de kubernetes: Kubernetes es una plataforma de orquestacion de codigo abierto para automatizar las operaciones de contenedores de linux, como la implementacion, administracion y escalado de aplicaciones de contenedores
	1. Comando para instalar el agente Cortex XDR dentro de Kubernetes **kubectl apply -f cortex-xdr.yaml**
	   
3. Instalacion y actualizaciones
	1. Configuracion inicial: Cree un paquete de instalacion del agente en consola, mueva el paquete a los puntos finales.
	2. Actualizacion de software del agente: Posible actualizar varios agentes desde la consola, se puede definir una implementacion diferida de la actualizacion automatica, Posible realizar seguimiento en el campo ESTADO de que actualizacion de agente fallo y crear acciones para uno o mas de los agentes con errores, Centro de actividades y registros de auditoria de agentes pueden realizar seguimiento de agentes fallidos.
	3. Actualizacion de contenido: Distinguir contenido de: actualizaciones dinamicas y actualizaciones de SW,  las actualizaciones de contenido contienen firmas nuevas y actualizadas, las actualizaciones de contenido se envian automaticamente a los agentes, la configuracion del contenido se puede retrasar de 1 a 30 dias.
	   
4. Actualizaciones de contenido: Las actualizaciones parciales permiten a los agentes recibir solo las nuevas incorporaciones y actualizaciones. Lista de posibles contenidos:
	1. Configuracion en los perfiles predeterminados
	2. Modelos y reglas de analisis local
	3. Listas de procesos protegidos de forma predeterminada
	4. Reglas de protecion contra amenazas conductuales
	5. Listas de firmantes conocidos de confianza
	6. Scripts utilizados por los agentes
	7. Bloquear los archivos listados por los firmantes
	8. Scripts de python proporcionados por Palo Alto Networks
	   
5. Actualizaciones periodicas: Por defecto desactivadas. Cuando está activado, el agente de Cortex XDR recibe actualizaciones de contenido menores. De lo contrario, los agentes de Cortex XDR seguirán recibiendo actualizaciones de contenido para las versiones principales.
   
6. Distribucion de agentes punto a punto: P2P
	1. Difusion de agentes del mismo nivel: Cuando un agente XDR intenta recuperar uan nueva version, transmitira sus agentes pares en la misma subred dos veces, una en la primera hora y otra en las siguientes 5 hrs.
	2. Descargar fuente: En configuracion/informacion general/fuente de descarga puede elegir la fuente de descarga de la que los agentes recuperan la actualizaciones: P2P, VM de brokers (si esta configurado), servidor de cortex XDR
	   
7. Comunicacion entre la instancia de cortex XDR y los agentes: Hay dos tipos de protocolo diferenes que usan XDR y agentes XDR para comunicarse:
	1. Basado en HTTPS: Usado cuando el agente inicia la comunicacion para los casos, incluido el envio de un latido periodico o de los datos de preencion de alertas a la instancia de cortex XDR despues de un ataque.
	2. Basado en WebSocket: Protocolo de comunicacion full duplex con estado que permite la comunicacion interactiva bidireccional entre una instancia XDR y agentes XDR.

![[Pasted image 20250110135923.png]]
