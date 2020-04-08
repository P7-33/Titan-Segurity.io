---
title: 'Los enrutadores TP-Link brindan a los ciberatacantes una puerta abierta
a las redes empresariales'
date: 2019-12-19T15:35:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-UID9e0t-7tQ/XfuKIMKOKiI/AAAAAAAALgQ/Lnx-tKlOPcQgULkE2D1mGXIU2vbhrH8KQCLcBGAsYHQ/s640/shodan-iot-search-featured.jpg)](https://1.bp.blogspot.com/-UID9e0t-7tQ/XfuKIMKOKiI/AAAAAAAALgQ/Lnx-tKlOPcQgULkE2D1mGXIU2vbhrH8KQCLcBGAsYHQ/s1600/shodan-iot-search-featured.jpg)

  

Los atacantes remotos pueden comprometer fácilmente el dispositivo y moverse lateralmente a través de LAN o WAN.

  

Una vulnerabilidad de firmware en los enrutadores TP-Link Archer C5 v4 (utilizados en entornos empresariales y domésticos) podría permitir el acceso remoto no autorizado al dispositivo con privilegios administrativos.

  

El error (CVE-2017-7405) afecta a los modelos que ejecutan la versión de firmware 3.16.0 0.9.1 v600c.0 Build 180124 Rel.28919n. Descubierto por primera vez por Grzegorz Wypych de IBM X-Force Red, podría permitir que un atacante remoto se propague lateralmente a través de una red, primero tomando el control de la configuración del enrutador a través de Telnet en la LAN y luego conectándose a un servidor de protocolo de transferencia de archivos (FTP) en otro lugar en la LAN

  

"Si se coloca en la red de la empresa, un enrutador comprometido puede convertirse en un punto de entrada para un atacante, y un lugar para pivotar desde la táctica de reconocimiento y movimiento lateral", escribió en una publicación de blog sobre la falla esta semana. "El riesgo es mayor en las redes empresariales donde los enrutadores como este se pueden utilizar para habilitar el Wi-Fi de invitado".

  

Agregó que "la conclusión es que el dispositivo de la víctima, FTP (si está configurado para usarse en WAN) y Telnet (solo LAN) pueden quedar completamente expuestos a un atacante".

  

La falla se puede explotar enviando solicitudes de CGI HTTP especialmente diseñadas al enrutador que contiene una solicitud de contraseña que es más corta o más larga que la cadena esperada. En el primer caso, el valor de la contraseña se distorsiona en bytes que no son ASCII, lo que corrompe el archivo de contraseña y causa un problema de denegación de servicio; en el último caso, anula el requisito de contraseña del dispositivo por completo y reemplaza la cadena con un valor vacío.

  

“\[Con\] la cadena corta ... el resultado es que el usuario no podrá iniciar sesión, y tampoco el atacante. Este problema afecta a Telnet, FTP y el servicio web ”, explicó el investigador. “\[Con la cadena larga\], la contraseña se anuló por completo y el valor ahora estaba vacío. A partir de este momento, pudimos acceder a Telnet y FTP sin ninguna contraseña, utilizando solo "admin" como nombre de usuario, que es el único usuario disponible en el dispositivo de forma predeterminada ".

  

Este dispositivo TP-Link solo presenta un tipo de usuario, administrador con privilegios de root, y el usuario ejecuta todos los procesos bajo este nivel de acceso, señaló.

  

Después de obtener acceso administrativo, Wypych descubrió que también es posible administrar de forma remota el enrutador a través de una conexión HTTPS segura, que "también es vulnerable a este ataque CGI", dijo Wypych.

  

La adquisición y el acceso privilegiado a la red es un resultado de una explotación, pero un usuario legítimo también quedaría bloqueado.

  

"\[El usuario\] ya no podrá iniciar sesión en el servicio web a través de la interfaz de usuario, ya que esa página ya no aceptará ninguna contraseña", señaló el investigador. “En tal caso, la víctima podría perder el acceso a la consola e incluso a un shell, y por lo tanto no podría restablecer una nueva contraseña. Incluso si hubiera una manera de establecer una nueva contraseña, la próxima solicitud LAN / WAN / CGI vulnerable, una vez más, anularía la contraseña. Por lo tanto, el único acceso serían los archivos FTP a través de una conexión de puerto USB ".

  

El error TP-Link es solo el último ejemplo de problemas endémicos en la seguridad de Internet de las cosas (IoT).

  

"Hoy en día, casi todos los hogares usan un enrutador, pero cinco de cada seis enrutadores no se actualizan adecuadamente por fallas de seguridad, según un estudio del American Consumer Institute", señaló Wypych. “Cuando surgen estos defectos, exponen a millones de usuarios domésticos y comerciales al riesgo de comprometer los datos. Y no solo se puede perder información textual: piense en imágenes de cámaras web, monitores para bebés y otros dispositivos conectados en el hogar que usan el mismo enrutador para conectarse a Internet ".

  

En este caso, TP-Link ha emitido parches para corregir el error en la versión TP-Link Archer C5 v4 y otras versiones (Archer MR200v4, Archer MR6400v4 y Archer MR400v3) que pueden estar en riesgo.

  

"Con cualquier dispositivo con conexión a Internet, es importante que las organizaciones estén al tanto de los parches y actualizaciones disponibles para sus sistemas", dijo James McQuiggan, defensor de la conciencia de seguridad en KnowBe4, por correo electrónico. “Los atacantes siempre están buscando dispositivos vulnerables con conexión a Internet y con cualquier vulnerabilidad conocida, se agregará a su arsenal de exploits para usar contra las organizaciones. Las organizaciones deben implementar el parche lo antes posible utilizando los procedimientos de gestión de cambios de su programa de seguridad. Si las organizaciones no implementan estos parches, aumentan su riesgo de ataque y posible violación de datos de sus redes y sistemas ".  
  
  

Fuente: [https://threatpost.com/](https://threatpost.com/tp-link-routers-cyberattackers-open-door/151254/)

No olvides Compartir... 

  
  
Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)