#subnodo

Consta de dos pasos
1. **Definir la condición de la regla y establecer un nombre de regla**: Definira la condicion de regla que consta de indicadores de amenaza y un nombre de regla BIOC. Definir una condicion regla BIOC es lo mismo que crear una busqueda de consulta, solo que BIOC genera alerta. 
   
   En la consola de admin hacer clic en **+Agregar BIOC**, se presentaran dos opciones para especificar la concicion de la regla: Usar XQL search o usar consultas de busqeda basadas en formularios.
   
   USO de busqueda XQL: Puede utilizar la busqueda XQL para definir las condiciones de las reglas BIOC, tega en cuenta las limitaciones:
   - No se puede utilizar toda la sintaxis XQL en BIOC XQL
   - Solo dos conjuntos de datos XDR_data y cloud_audit_log, estan disponibles para BIOC XQL.
    
    BIOCs basados en formularios: Otra forma es seleccionar un tipo de recurso de la lista poporcionada e introducir los parametros de busqueda relacionados. Tipos de entidades: Proceso, archivo, red, Carga de imagen y registro.
    
	Tipo de archivo: Formulario BIOC
	![[Pasted image 20241209121611.png]]

2. **Especificar otros parametros de regla**: Se especifican los parametros de regla restantes relacionados con alertas, gravedad y el tipo, que generaran alertas si se encuentran en una coicidencia de regla. ![[Pasted image 20241209121950.png]]
