La zona actual no cuenta con espacio para correr la VM por lo que se debe de cambiar la zona.

En algunas ocasiones debido a la configuración o a los requerimientos de la VM en algunas zonas no será posible montar la VM por lo que se debe de buscar la mas optima, se puede usar el siguiente comando en la consola Azure:

`az vm list-skus --location eastus --size Standard_E4as_v5 --output table`


[[Azure]]
