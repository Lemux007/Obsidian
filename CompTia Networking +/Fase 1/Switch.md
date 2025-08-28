#Nodo
Se encarga de reenviar el trafico en la red, trabaja principalmente con [[MAC]] addresses por lo que esta basado en capa 2 (Data link).

Operan mayormente en Hardware, por medio de un [[ASIC]](Application Specifc Integrated Circuit).

***Pueden proveer de energía a través del cable ethernet PoE(Power over Ethernet)***

Puede ser un switch capa 3 (Network) si incluye alguna funcionalidad tipo router.

Cuando un dispositivo envía paquetes de datos al switch este relaciona su [[MAC]] addresses con el puerto en el que lo esta enviando, por lo que si alguien envía paquetes a este mismo dispositivo con su [[MAC]] addresses el switch lo manda al puerto que tiene guardado en su tabla, en el caso que no tenga registro de el destinatario genera flooding o inunda todos los puertos (menos el de entrada).



