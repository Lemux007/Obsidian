#Nodo

1. La activación de Cortex XDR crea una nueva instancia de Cortex XDR, también conocida como inquilino. La activación es una tarea única que finaliza con el aprovisionamiento de bases de datos y servicios de middleware basados en la nube. El superusuario recibe un correo electrónico de activación que contiene un enlace a Cortex Gateway. Para poder activar una instancia de Cortex XDR en una cuenta de CSP, se le debe asignar un rol de administrador de cuenta de XDR obligatorio.
   
   Para activar una instancia ir a **Tenant navigator > Cortex > gateway > Disponible para la activacion**, buscar el numero de serie y click en activar  el gateway esta en https://xdr-gateway.paloaltonetworks.com/

2. Configuracion de la instancia: Atributos para un inquilino mediante cortex Gateway:
   - Nombre del inquilino, descriptivo para la instancia
   - Region: Donde se dessea instalar la instancia de XDRy todos los servicios de infraestructura dependientes incluida Cortex Data Lake
   - Subdominio de inquilino: Nombre de un subdominio unico en la region. valido en la especificacion de dominio completo (FQDN)
     
     Las especificaciones de la región y el subdominio del inquilino forman una dirección HTTPS única para la instancia de Cortex XDR, a la que puede acceder en https://subdominio.xdr.region.paloaltonetworks.com.

3. Verificacion de instancias: **Cortex Gateway > Inquilino disponible** y estatus activo
