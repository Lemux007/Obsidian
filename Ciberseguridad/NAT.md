Network Address Translation.
Es el proceso en el que el router reescribe parte de la dirección IP privada para poderla asociar a la IP publica para así poder acceder o comunicarse a internet.

- Cambia la IP origen y el puerto origen en el trafico saliente
- Cambia la IP destino y puerto destino en el trafico entrante.

==Trafico Saliente==

1. El router NAT cambia la IP privada por la IP publica y así el EP que recibe el datagrama cree que el origen es el router NAT.
2. El router mantiene una tabla con los cambios que se realizaron para el trafico saliente y así cuando se reciba una respuesta o trafico entrante ya se se tenga la información de los cambios.
3. Si otro maquina usa el mismo puerto el router debe de escoger otro y modificar el datagrama 
4. Cuando se recibe respuesta la router NAT cambia la IP destino y el puerto destino basandose en la tabla con los correspondientes a la IP interna y el puerto interno.

==Trafico Entrante==
Cuando se recibe un datagrama que no es una respuesta no es posible identificar el destino (IP, puerto) en la tabla por lo que se descarta.

Soluciones:

1. Se asigna una IP para todo el trafico entrante que no es respuesta.
2. Generar entradas predeterminadas en la tabla NAT para los datagramas en base al puerto al que va dirigido.

