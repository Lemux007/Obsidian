#Nodo

1. Pagina de administracion de politicas: Desde endpoint>>Policy Managment, XDR ofrece 3 secciones para administrar reglas y politicas:
	![[Pasted image 20241203095956.png]]
2. Perfiles de prevención predeterminados: XDR proporciona un perfil predeterminado para cada tipo de perfil con el fin de iniciar de inmediato la protección de los terminales. ![[Pasted image 20241203100606.png]] 
	1. Agent Settings: Contiene configuraciones que especifican como funcionan normalmente los agentes de XDR, como limites en el espacio de registro en los terminales, hailitar la recopilacion mejorada de datos terminales EED o establecer una nueva contraseña de supervisor.
	2. Exploit: Este perfil puede bloquear fallas del sistema en los navegadores como kits de exploits.
	3. Malware: Deshabilita las cargas de archivos en wildfire o habilitar la cuarentena de los mismos.
	4. Restricciones: Puede bloquar intentos de ejecutar archivos desde uan USB o capertas desconocidas
	5. Exceptions: Deshabilitacion de modulos de proteccione contra vulnerabilidades de seguridad para un proceso especifico que se habilito globalmente en un perfil de vulnerabilidad. 
3. Gestion de perfiles de prevencion, importar y exportar un perfil desde los puntos de conexion > administracion de politicas > perfiles > prevencion