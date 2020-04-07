---
title: 'El troyano de Android que deshabilita a Google Play Protect'
date: 2020-01-13T17:04:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Msq6xOew0kA/XhySrOrA5VI/AAAAAAAALnY/b_tGOsp27TcbThD7sqyufEZdHll1ZGg-QCLcBGAsYHQ/s640/0_android-malware.jpg)](https://1.bp.blogspot.com/-Msq6xOew0kA/XhySrOrA5VI/AAAAAAAALnY/b_tGOsp27TcbThD7sqyufEZdHll1ZGg-QCLcBGAsYHQ/s1600/0_android-malware.jpg)

  

Una cepa de malware de Android camuflada como una aplicación del sistema esta siendo utilizada para deshabilitar el servicio Google Play Protect, generar revisiones falsas, instalar aplicaciones maliciosas, mostrar anuncios y más.

  

El malware muy ofuscado denominado Trojan-Dropper.AndroidOS.Shopper.a utiliza un icono del sistema y el nombre de ConfigAPK que se parece mucho al nombre de un servicio legítimo de Android responsable de la configuración de la aplicación la primera vez que se inicia un dispositivo.

  

"Trojan-Dropper.AndroidOS.Shopper.a estuvo más extendido en Rusia, donde la mayor proporción de usuarios infectados (28.46%) se registró en octubre - noviembre de 2019", dijo el investigador de Kaspersky Lab, Igor Golovin. "El segundo lugar fue para Brasil (18,70%) y el tercero para India (14,23%)".  
  

[![](https://1.bp.blogspot.com/-fN9Hs0zFDbw/XhySgXSLcXI/AAAAAAAALnU/OLVCLAuK2cEBGl3lZE7KMvvOATnt9gE3wCLcBGAsYHQ/s640/Shopper_a-spread.png)](https://1.bp.blogspot.com/-fN9Hs0zFDbw/XhySgXSLcXI/AAAAAAAALnU/OLVCLAuK2cEBGl3lZE7KMvvOATnt9gE3wCLcBGAsYHQ/s1600/Shopper_a-spread.png)

Imagen: _Kaspersky Lab_

  

**Servicios de promoción de Malicious Play Store**  

Una vez que infecta el dispositivo Android de la víctima, el malware descarga y descifra el payload, luego pasa directamente a la recolección de información, como el país, el tipo de red, el proveedor, el modelo de teléfono inteligente, la dirección de correo electrónico, IMEI e IMSI.

  

  

Todos estos datos se extraen luego a los servidores de los operadores que enviarán una serie de comandos para que se ejecuten en el teléfono inteligente o tableta infectados.

  

Los atacantes utilizarán el troyano Shopper.a para aumentar las calificaciones de otras aplicaciones maliciosas en Play Store, publicar revisiones falsas en las entradas de cualquier aplicación, instalar otras aplicaciones de Play Store o tiendas de aplicaciones de terceros.

  

Todo esto se hace abusando del Servicio de Accesibilidad, una táctica conocida utilizada por el malware de Android para realizar una amplia gama de actividades maliciosas sin necesidad de la interacción del usuario. Si no tiene permisos para acceder al servicio, el troyano usará phishing para obtenerlos del propietario del dispositivo comprometido.

  

El malware también deshabilita el servicio de protección contra amenazas móviles Google Play Protect, la protección contra malware Android integrada de Google, para que pueda realizar sus actividades sin problemas.

  

"Google Play Protect analiza más de 50 mil millones de aplicaciones todos los días en más de dos mil millones de dispositivos", según el informe de revisión anual de seguridad y privacidad de 2018 de Android publicado en marzo de 2019.  
  

[![](https://1.bp.blogspot.com/-jma4NMercK0/XhySzsYUEwI/AAAAAAAALng/W55VXoZIzKkywrIWQrYi7JGUTHosq44zQCLcBGAsYHQ/s640/Shopper_a-receiving-commands.png)](https://1.bp.blogspot.com/-jma4NMercK0/XhySzsYUEwI/AAAAAAAALng/W55VXoZIzKkywrIWQrYi7JGUTHosq44zQCLcBGAsYHQ/s1600/Shopper_a-receiving-commands.png)

Shopper.a receiving commands (_Kaspersky Lab_)

  

"La falta de derechos de instalación de fuentes de terceros no es un obstáculo para el troyano: se otorga los permisos necesarios a través del Servicio de Accesibilidad", explicó el investigador de Kaspersky Lab, Igor Golovin.

  

"Con permiso para usarlo, el malware tiene posibilidades casi ilimitadas para interactuar con la interfaz del sistema y las aplicaciones. Por ejemplo, puede interceptar los datos que se muestran en la pantalla, hacer clic en los botones y emular los gestos del usuario".

  

Dependiendo de los comandos que recibe de sus maestros, Shopper.a puede realizar una o más de las siguientes tareas:

  

• Abra los enlaces recibidos del servidor remoto en una ventana invisible (mediante la cual el malware verifica que el usuario esté conectado a una red móvil).

• Después de desbloquear cierto número de pantallas, escóndete del menú de aplicaciones.

• Verifique la disponibilidad de los derechos del Servicio de accesibilidad y, si no se otorgan, emita periódicamente una solicitud de phishing para que el usuario los proporcione.

• Desactivar Google Play Protect.

• Crear accesos directos a sitios anunciados en el menú de aplicaciones.

• Descargue aplicaciones del "mercado" de terceros Apkpure\[.\]com e instálelas.

• Abra las aplicaciones anunciadas en Google Play y haga clic para instalarlas.

• Reemplazar accesos directos a aplicaciones instaladas con accesos directos a sitios anunciados.

• Publique reseñas falsas supuestamente del usuario de Google Play.

• Mostrar anuncios cuando la pantalla está desbloqueada.

• Registre usuarios a través de sus cuentas de Google o Facebook en varias aplicaciones.

  

"Los ciberdelincuentes usan Trojan-Dropper.AndroidOS.Shopper.a para aumentar la calificación de ciertas aplicaciones y aumentar la cantidad de instalaciones y registros", agregó Golovin.

  

"Todo esto se puede utilizar, entre otras cosas, para engañar a los anunciantes. Además, el troyano puede mostrar mensajes publicitarios en el dispositivo infectado, crear accesos directos a sitios de anuncios y realizar otras acciones".

  

En noticias relacionadas, Google reveló que Play Protect detectó y eliminó alrededor de 1.700 aplicaciones infectadas con el malware Android Joker (también conocido como Pan) de Play Store desde que la compañía comenzó a rastrear esta cepa a principios de 2017.

  

Para poner las cosas en perspectiva, mientras que la revisión anual de Android Security & Privacy 2018 no proporcionó el número exacto de aplicaciones maliciosas eliminadas, la de 2017 afirma que la compañía "eliminó más de 700,000 aplicaciones que violaron las políticas de Google Play, un 70% más que las aplicaciones eliminadas en 2016 ".

  
  

Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/android-trojan-kills-google-play-protect-spews-fake-app-reviews/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)