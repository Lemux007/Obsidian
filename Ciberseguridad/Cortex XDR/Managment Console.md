DESCRIPCION GENERAL DE LA CONSOLA DE ADMINISTRACION CORTEX XDR
1. Acceso a la consola: https:// subdominio.xdr | region.paloaltonetworks.com, para autenticarse especificar usuario y contraseña de CSP
2. Panel de navegacion: Paneles de control e informes, Respuesta a incidentes, Reglas de deteccion, assets, endpoinst.
3. Configuracion y ajustes de seguridad de la sesion: 
	1. Configuracion de seguridad: Config/configuraciones/general/configuracion de seguridad
	2. Sesion de caducidad: Establecer tiempo de sesion abierta
	3. Sesiones permitidas: Permite restringir a los usuarios CSP puedan conectarse a la consola de administracion
	4. Caducidad del usuario: Permite desactivar usuarios inactivos
4. Componentes principales de los paneles de control e informes:
	1. Panel: Contiene widgets que resumen la informacion en graficos
	2. Informes: Puede ver los informes que se han ejecutado
	3. Administrador de paneles: Para modificar paneles
	4. Plantilla de informes: Crear nuevas plantillas de informes o editar existentes
	5. Biblioteca de widgets


QUICK LAUNCHER
	Usado para buscar objetos y paginas de consola. Es decir el tipo de dominio, punto de conexion, nombre de archivo, ruta de archivo, hash, direccion IP, marca de tiempo o nombre de usuario.
1. Acciones dependientes de QUICK LAUNCHER
	1. Investigar
	2. Accion


PAGINAS TIPICAS DE LA CONSOLA DE ADMINISTRACION
1. Formato Tabular: Muestran acciones relacionadas con la tabla como ordenar, filtrar, actualizar y finalizar la exportacion. Opciones:
	1. Opciones de desplazamiento 
	2. Acciones de tabla
	3. Opciones de seleccion unica y multiple
	4. Capacidades de filtrado


GESTION DE ENDPOINTS
1. Endpoints: Un endpoint administrado es cualquier sistema en el que este instalado y registrado u agente XDR. una vez instalado en un terminal, el agente se conecta a la instancia, solicita licencia y se registra como un producto con licencia.
2. Grupos de endpoints: Permiten aplicar facilmente reglas de politicas a un conjunto de edps. Tipos:
	1. Estatico
	2. Dinamico


INSTALACION DEL AGENTE
1. Flujo de implementacion de agentes
	1. Crear un paquete de instalacion
	2. Descargar paquete en el punto de conexion: Usar 63 o 32 bits installer
	3. Ejecutar paquete: Transferir al punto de conexion deseado y ejecutar para instalar.



