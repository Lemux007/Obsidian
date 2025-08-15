Listas dinamicas externas (EDL): Tipo de lista de bloqueo en la que cada linea es una direccion IP separada o una entrada de nombre de host que se va a bloquear.
   - Consumidores tipicos de EDL son NGFW (PAN-OS)

2. Tareas de servicio EDL: EDL tiene una configuracion global **Configuracion > Integracion**, como una tarea de una sola vez, la configuracion incluye la habilitacion global del servicio EDL de cortex XDR.
   sd
   - Despues de establecer el parametro EDL hay dos tareas de administrador diferentes en curso: Agregar direcciones IP y dominios a las listas EDL y administrar las listas EDL
   - Puede agregar direcciones IP y dominios maliciosos a las listas de EDL desde varias paginas de la consola de administracion, incluido el centro de actividades menu de respuesta > EDL
   - Puede administrar las listas d eEDL desde el **Centro de actividades > acciones aplicadas actualmente > Lista dinamica externa**
	
	Configuracion global de EDL
	- Config de autenticacion para conectarse al servicio EDL
	- Boton de activacion/desactivacion para el servicio EDL
	- Las URL de las dos listas EDL: Direcciones IP EDL y nombres de dominio EDL
	- Formato de URL. https://edl-|subdominio|.xdr|region|.paloaltonetworks.com/block_list?type=ip

3. Adicion de direcciones IP Y HOST A EDL
   Puede agregar direcciones IP y dominios maliciosos a las listas de EDL desde varias paginas de la consola de administracion. 
   **Respuesta > EDL**
   **Centro de actividades > Agregar EDL**
   **Quick Launcher**
   **vista de IP**

4. Gestion de EDL en el centro de accion
   A medida que se agrega ip y dominios a las EDL cortex mantiene sus adiciones en dos listas accesibles desde **Centro de actividades > Acciones aplicadas actualmente > Lista dinamica externa**