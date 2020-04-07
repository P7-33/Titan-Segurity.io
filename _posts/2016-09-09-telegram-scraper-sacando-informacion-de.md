---
title: 'Telegram Scraper. Sacando información de usuarios de Telegram'
date: 2020-02-09T05:10:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-jTDRbgNdsKg/XkA9QF-om9I/AAAAAAAALwk/8uiXf7p57ngr064vwT6WHZpeswsH7pwHgCLcBGAsYHQ/s640/ddr-telegram-scraper-e1579908265497.png)](https://1.bp.blogspot.com/-jTDRbgNdsKg/XkA9QF-om9I/AAAAAAAALwk/8uiXf7p57ngr064vwT6WHZpeswsH7pwHgCLcBGAsYHQ/s1600/ddr-telegram-scraper-e1579908265497.png)

  

En el artículo de hoy os traemos un scraper para obtener información de usuarios en grupos de Telegram, vamos a ver como aprovechar el domingo de cacharreo!! 

  

Aparentemente puede parecer poca cosa, pero, gracias a los datos que nos da, no solo podremos crear nuestros scripts automáticos, si no que además podremos por ejemplo, obtener información adicional de usuarios. Con esto podemos descubrir el ID original de un usuario para reportarlo o para ver si es un usuario que ha cambiado de nombre.

  

Enlace del proyecto: [https://github.com/th3unkn0n/TeleGram-Scraper](https://github.com/th3unkn0n/TeleGram-Scraper)  

Para instalarlo, en nuestra máquina Linux abrimos la consola y ponemos:

**git clone [https://github.com/th3unkn0n/TeleGram-Scraper.git](https://github.com/th3unkn0n/TeleGram-Scraper.git)**

Una vez tenemos el proyecto debemos ir siguiendo los siguientes pasos.

Primero vamos a la API de Telegram a conseguir nuestras credenciales: [https://my.telegram.org/](https://my.telegram.org/). Una vez aquí, debemos ir completando los registros para obtener las claves.

  
  

![](https://i0.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura2-1.png?fit=770%2C418&ssl=1)

Después pulsamos sobre la primera opción:

  
  

![](https://i1.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura3.png?fit=770%2C326&ssl=1)

Y seguimos completando los campos necesarios:

  
  

![](https://i2.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura4.png?fit=770%2C543&ssl=1)

Pulsamos en crear aplicación y nos saldrán nuestras claves. Es muy importante que no se compartan, esto daría acceso total a nuestro Telegram.

Nota: para el uso de esta aplicación deberemos quitar la verificación en dos pasos. Que no tiene nada que ver con el mensaje que ya llega a Telegram por defecto al entrar desde otros equipos.

  
  

![](https://i2.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura5.png?fit=770%2C406&ssl=1)

Vamos ahora siguiendo los siguientes pasos. Accedemos a la carpeta desde la consola. Dentro de el directorio ponemos los siguientes comandos:

Install requierments  
**python3 setup.py -i**

  
  

![](https://i0.wp.com/derechodelared.com/wp-content/uploads/2020/01/image-10.png?fit=770%2C440&ssl=1)

Tras esto, para el archivo de configuración:

Setup configration file  
**python3 setup.py -c**

  
  

![](https://i1.wp.com/derechodelared.com/wp-content/uploads/2020/01/image-11.png?fit=770%2C439&ssl=1)

Aquí meteremos las claves obtenidas en la API. El teléfono debemos ponerlo con la extensión incluida, es decir justo así «**+34999999999**«.

Una vez esté esto completado nos pedirá el código que nos llega al Telegram.

  
  

![](https://i2.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura7.png?fit=770%2C442&ssl=1)

Una vez esté eso completado podremos ejecutar el programa.

**python3 scraper.py**

Esto nos sacará toda la información sobre los usuarios del grupo que nos saldrá de la siguiente manera:

  
  

![](https://i2.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura8.png?fit=770%2C343&ssl=1)

Si queremos ver la información recolectada bastará con acceder al archivo «**members.csv**«.

  
  

![](https://i2.wp.com/derechodelared.com/wp-content/uploads/2020/01/Captura9.png?w=770&ssl=1)

No vamos a explicar más, pero, si que nos vamos a quedar sacando ideas nuevas de uso para esta herramienta… podremos por ejemplo, con esta información y haciendo uso de la API, monitorizar usuarios, crear alertas sobre los mismos, crear o borrar mensajes…   
  

Fuente: [https://derechodelared.com/](https://derechodelared.com/telegram-scraper/#.Xj8gAR7hW0k.twitter)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)