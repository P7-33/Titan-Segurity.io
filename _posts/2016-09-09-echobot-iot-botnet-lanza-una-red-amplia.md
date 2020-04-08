---
title: 'Echobot IoT Botnet lanza una red amplia con una serie de adiciones de
exploit'
date: 2019-12-17T03:32:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-4647bFTMR6s/Xfg9yImhSCI/AAAAAAAALfU/lEkliTZjoykn2xsMi5SQEBuCOtaDi_0ngCLcBGAsYHQ/s400/botnet-e1573740377341.jpg)](https://1.bp.blogspot.com/-4647bFTMR6s/Xfg9yImhSCI/AAAAAAAALfU/lEkliTZjoykn2xsMi5SQEBuCOtaDi_0ngCLcBGAsYHQ/s1600/botnet-e1573740377341.jpg)

  

Se han agregado 13 nuevos exploits a la bolsa de trucos del malware.  
  
Según los investigadores, una variante de la botnet Mirai Internet of Things (IoT) conocida como "Echobot" ha agregado 13 vulnerabilidades más a su bolsa de trucos de infiltración. Estos apuntan a una gama de dispositivos, incluidos enrutadores, firewalls, cámaras IP, utilidades de administración de servidores, un controlador lógico programable utilizado en entornos industriales, un sistema de pago en línea e incluso una aplicación web Yachtcontrol.  
  
Las nuevas incorporaciones van desde los CVE antiguos (uno de 2006 es para firewalls de spam Barracuda) hasta un error que se reveló a principios de diciembre. Traen la última versión del código malicioso para tener un total de 71 exploits únicos.  
  
Las botnets de IoT están empeñadas en infectar los dispositivos conectados para reunir sus recursos para llevar a cabo diversas actividades nefastas, como llevar a cabo ataques distribuidos de denegación de servicio (DDoS). Como tal, lanzar una red amplia es una estrategia inteligente para escalar la botnet.  
  
"Uno podría arriesgarse a adivinar que los atacantes podrían estar apuntando a los puntos débiles de las vulnerabilidades de IoT, apuntando a los dispositivos heredados que todavía están en uso pero probablemente demasiado viejos para actualizarlos debido a problemas de compatibilidad y vulnerabilidades más recientes que son demasiado recientes para que los propietarios han parcheado ", según los investigadores de la división Unidad 42 de Palo Alto Networks, en una publicación reciente.  
  
Uno de los errores más inusuales incluye CVE-2019-17270, un error de ejecución remota de código en los servidores web de Yachtcontrol mencionados anteriormente, que permiten a los propietarios de yates controlar de forma remota las funciones de sus embarcaciones.  
  
"Es posible ejecutar comandos directos del sistema operativo como un usuario no autenticado a través de la página y el parámetro '/pages/systemcall.php?command={COMMAND}', donde {COMMAND} se ejecutará y devolverá los resultados al cliente", según al aviso de error.  
  
CCBill Online Payment Systems también fue el objetivo de la nueva versión; CCBill maneja pagos de comercio electrónico en línea para alrededor de 30,000 minoristas electrónicos, según su sitio web.  
  
Y, Echobot ha agregado un exploit para un error de inyección de comandos en el producto Citrix NetScaler SD-WAN utilizado por las empresas para conectar ubicaciones de sucursales.  
  
La última versión apareció en octubre "por un par de horas" con 11 errores nuevos antes de que volviera a estar fuera de línea, según la Unidad 42; luego resurgió a principios de diciembre con dos exploits adicionales.  
  
"Estas vulnerabilidades no se habían visto previamente explotadas en la naturaleza antes de esta versión", según la publicación.  
  
Las variantes de Mirai continúan apareciendo; En octubre de 2016, el malware Mirai se propagó a los dispositivos IoT obteniendo acceso mediante contraseña y nombres de usuario predeterminados. El malware luego conectó los dispositivos afectados a una red de bots y realizó ataques DDoS. El mayor de estos ataques inundó al proveedor de DNS Dyn, causando que varios sitios web conocidos se apagaran durante horas. El código fuente de Mirai se filtró posteriormente, lo que provocó el surgimiento de varias otras redes de bots imitadores, incluido Echobot.  
  

Fuente: [https://threatpost.com/](https://threatpost.com/echobot-iot-botnet-exploit-additions/151154/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)