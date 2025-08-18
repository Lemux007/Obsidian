==Web Single Sign-On o Web Access Management==
Funciona con aplicaciones a los que se acceden en la Web.
Cuando se intenta acceder se recoge la solicitud con un proxy o por otro medio para separar a los usuario que no se han autenticado y los que ya están autenticados, los no autenticados son enviados a un servidor de autenticación y solamente son redirigidos cuando se identificaron correctamente, aquí se utilizan las cookies para "recordar" a los usuarios autenticados y su estado de autenticación.

Ejemplos:

==Kerberos:== El usuario se registra en el servidor Kerberos y recibe un "ticket" que las aplicaciones usan para autenticar al usuario.

==Open ID:== Proceso SSO que guarda en la URL la autenticación del usuario. 

Opción para uso de [[Certificado Digital]]

