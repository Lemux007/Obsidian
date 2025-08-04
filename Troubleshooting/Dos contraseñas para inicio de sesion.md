El usuario ==**remoto**== presenta constantes bloqueos de inicio de sesión en VPN, y se hacen numerosos reinicios y desbloqueos de credenciales, finalmente el usuario comenta que ha estado ingresando con dos contraseñas de inicio de sesión una para ingresar al equipo y otra para conectar a la VPN, no ha asistido a site en un tiempo prolongado de tiempo

**Solución:**
Es necesario sacar y volver a incluir a dominio el equipo del usuario para que se genere una actualización de credenciales, ya que no se ha conectado directamente a la red en un periodo largo, solo se ha conectado por VPN.

Debido a que se pierde la conexión de a la red cuando se saca de dominio y es necesario estar conectado la primera vez que se inicia sesión después de agregar a dominio pueden presentarse problemas para mantener la conexión a la vpn en otros usuarios por lo que para que el sistema guarde el cache de las credenciales en el sistema se debe de abrir un CMD del usuario que se desea agregar con el siguiente comando en la cuenta local del equipo con la vpn activa:

`runas /user:intranova.com.mx\usuario cmd`

Solicitara contraseña del usuario, posteriormente ya se puede ingresar en el inicio de sesiones de la pantalla de bloqueo.

