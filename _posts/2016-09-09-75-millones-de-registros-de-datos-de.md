---
title: '7,5 millones de registros de datos de usuario de Adobe Creative Cloud
expuestos'
date: 2019-10-28T03:17:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-i6EE3oWnyLo/XbdIcI2FoTI/AAAAAAAALMo/mDpJQ_9Ww7k9b2NCvdeYwAabQoLBXjiDwCLcBGAsYHQ/s640/1.png)](https://1.bp.blogspot.com/-i6EE3oWnyLo/XbdIcI2FoTI/AAAAAAAALMo/mDpJQ_9Ww7k9b2NCvdeYwAabQoLBXjiDwCLcBGAsYHQ/s1600/1.png)

  

Adobe aseguró una base de datos con 7,5 millones de registros pertenecientes a los usuarios de Adobe Creative Cloud. El caché no estaba protegido de ninguna manera, lo que permitía a cualquiera acceder a la información del cliente si sabían cómo encontrarla.

  

Aunque los detalles incluidos no son muy confidenciales, podrían usarse para lanzar campañas de phishing mejor diseñadas contra clientes cuyos datos fueron expuestos.

  

**Adobe reaccionó rápidamente**  

No está claro cuánto tiempo estuvieron expuestos los detalles, pero Bob Diachenko, el investigador que lo descubrió, estima que cualquiera tuvo acceso libre a ellos durante aproximadamente una semana.  
  

Diachenko informó sus hallazgos a Adobe el 19 de octubre y la compañía aseguró la base de datos Elasticsearch el mismo día.

  

Según Comparitech, no se incluyeron detalles sensibles como contraseñas o datos de pago.

  

No hay información sobre si alguien accedió a la información, pero si lo hicieran, podrían usarla para campañas de phishing específicas.

  

El tamaño del caché, según una captura de pantalla proporcionada por los investigadores, es cercano a 86 GB

  

[![](https://1.bp.blogspot.com/-xIr3Nzt20_Q/XbdIhYnAgPI/AAAAAAAALMs/0T9b6TF77iM6AyOuVw7M8aLLO0YQonR0gCLcBGAsYHQ/s640/2.jpg)](https://1.bp.blogspot.com/-xIr3Nzt20_Q/XbdIhYnAgPI/AAAAAAAALMs/0T9b6TF77iM6AyOuVw7M8aLLO0YQonR0gCLcBGAsYHQ/s1600/2.jpg)

  

Una captura de pantalla tomada por Diachenko muestra los detalles a los que se puede acceder sin autenticación. Estos incluyen direcciones de correo electrónico, la fecha en que se creó la cuenta, los productos utilizados por el cliente y el estado del pago.

  

[![](https://1.bp.blogspot.com/-jqaeoLn64vI/XbdIlR0UhKI/AAAAAAAALMw/i0ne9C39mwwcGJCnarTtZ8rnKQLc32K7ACLcBGAsYHQ/s640/3.jpg)](https://1.bp.blogspot.com/-jqaeoLn64vI/XbdIlR0UhKI/AAAAAAAALMw/i0ne9C39mwwcGJCnarTtZ8rnKQLc32K7ACLcBGAsYHQ/s1600/3.jpg)

  

  

Los detalles adicionales almacenados en la base de datos que podrían influir en el éxito de una estafa incluyen los siguientes:

  

Estado de suscripcion

Si el usuario es un empleado de Adobe

ID de miembros

País

Tiempo desde el último inicio de sesión

  

El servidor abierto Elasticsearch de Adobe fue descubierto al escanear activamente la web en busca de bases de datos inseguras.

  

  

**Actualización \[25/10/2019, 18:20 ET\]:** Adobe publicó hoy una declaración sobre la base de datos expuesta diciendo que era parte de un "entorno prototipo" que estaba mal configurado. La compañía informa que el entorno almacenó información de clientes de Creative Cloud que no incluía contraseñas o detalles financieros.

  

"Este problema no estaba relacionado con, ni afectó, la operación de ningún producto o servicio principal de Adobe. Estamos revisando nuestros procesos de desarrollo para ayudar a prevenir que ocurra un problema similar en el futuro".  
  
  

Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/75-million-records-of-adobe-creative-cloud-user-data-exposed/)

No olvides Compartir...

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)