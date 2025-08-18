1. Configuraciones de Access Broker VM: ***Clic detecho en la VM > Administracion de agente > Configurar***
   - Maquinas virtuales de broker registrado: Muestra las maquinas virtuales de broker registradas en este inquilino de cortex xdr
   - Encabezados de columna: Muestran oara cada broker VM el nombre del dispositivo, la interfaz externa, todas las interfaces, la version del broker VM, estado de configuracion, uso de CPU, uso de memoria, uso del disco.
   - Columna aplicaciones: Estado de activacion de los applets de broker vm

2. Ver y editar detalles de configuracion: Los detalles de configuración se agrupan en categorías en la página Configuraciones de máquina virtual de agente. En esta sección se muestra cómo ver y editar las configuraciones asociadas a cada grupo. Los detalles de configuración se pueden ver incluso cuando la máquina virtual de Broker no está conectada a Cortex XDR. Sin embargo, estos detalles solo se pueden editar cuando la máquina virtual de Broker está conectada a Cortex XDR. Se accede a los grupos de configuración mediante selección desde el panel de navegación izquierdo de la página Configuraciones de VM de agente.
   - Nombre del dispositivo y su FQDN
   - Interfaces de red: En el panel de navegacion izquierdo, los detalles de config de la interfaz de red incluyen el nombre y la ip, MAC y si la direccion es estatica o dinamica.
   - Servidor proxy: Broker vm se puede configurar para usar un servidor proxy para comunicarse con cortex XDR o acceder a internet. Para configurar un proxy de maquina virtual de agente, seleccione **Servidor proxy** en el panel de navegacion izquierdo. Protocolos: Socks4 o socks5
   - Protocolo de tiempo de red (NTP): La configuracion de NTP es esencial para el registro correcto y para la sincronizacion del reloj entre el recopilador de syslog y otras aplicaciones y servicios.
   - Actualizacion automatica: Nuevas funciones y mejoras
   - Acceso SSH: Las conexiones ssh a la maquina virtual del agente se pueden habilitar o deshabilitar, el acceso ssh se autentica mediante una clave publica, concede acceso remoto a la instancia de vm de broker