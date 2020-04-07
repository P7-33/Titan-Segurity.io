---
title: 'Las víctimas de la botnet Mozi son enrutadores Netgear, D-Link, Huawei'
date: 2019-12-30T03:14:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-drHZeUm1_b0/XgldkpjcxGI/AAAAAAAALi8/6hA8n0mxJqg9OQOa5Z5Mp76iClVCnOtiQCLcBGAsYHQ/s640/system-2660914_960_720.jpg)](https://1.bp.blogspot.com/-drHZeUm1_b0/XgldkpjcxGI/AAAAAAAALi8/6hA8n0mxJqg9OQOa5Z5Mp76iClVCnOtiQCLcBGAsYHQ/s1600/system-2660914_960_720.jpg)

  
Los expertos de 360 ​​Netlab [informan](https://blog.netlab.360.com/mozi-another-botnet-using-dht/) que las botnets P2P son cada vez más frecuentes: los expertos han descubierto una nueva botnet Mozi P2P que destruye activamente los enrutadores Netgear, D-Link y Huawei, buscando contraseñas débiles a través de Telnet.

Los investigadores descubrieron una botnet hace unos cuatro meses y en el pasado han llegado a la conclusión de que su objetivo principal son los ataques DDoS. Mozi se creó utilizando el protocolo de Tabla de hash distribuido (DHT), que es ampliamente utilizado por los clientes de torrents y otras plataformas P2P. Esto permite que la botnet funcione sin servidores de comando, así como para ocultar el payload entre el tráfico DHT normal. Para garantizar la integridad y la seguridad de los componentes de la botnet, se utilizan ECDSA384 y el algoritmo XOR.

[![](https://1.bp.blogspot.com/-TP3NVDu-qUE/XgkEPwPZ9uI/AAAAAAAALiw/HPdLX8YxrTMvlBxrXHRtIJZYJeQWofsPgCLcBGAsYHQ/s640/Mozi-botnet-1.png)](https://1.bp.blogspot.com/-TP3NVDu-qUE/XgkEPwPZ9uI/AAAAAAAALiw/HPdLX8YxrTMvlBxrXHRtIJZYJeQWofsPgCLcBGAsYHQ/s1600/Mozi-botnet-1.png)

Como se mencionó anteriormente, el malware ataca dispositivos vulnerables a través de Telnet, verificando la seguridad de sus contraseñas. Si el ataque tiene éxito y se obtiene acceso, el malware Mozi se descarga en los dispositivos y el bot se une automáticamente a la red de bots. Luego, el bot recién creado recibe y ejecuta comandos del operador, y también comienza a buscar otros enrutadores vulnerables Netgear, D-Link y Huawei para comprometerse.

> "Después de que Mozi establece conexiones P2P utilizando el protocolo DHT, el archivo de configuración se sincroniza y las tareas correspondientes se inician de acuerdo con las instrucciones en el archivo", escriben los investigadores.

Entonces, Mozi es capaz de:

*   implementar ataques DDoS (este módulo usa el código del conocido Malvari Gafgyt, admite HTTP, TCP, UDP, etc.);
*   recopilar y robar información sobre bots (ID de bot, dirección IP, PUERTO, nombre de archivo, puerta de enlace, arquitectura del procesador);
*   ejecutar carga útil desde la URL especificada;
*   Actualizado a través de la URL especificada;
*   ejecutar comandos del sistema o personalizados.

La botnet también ataca a docenas de diferentes dispositivos potencialmente vulnerables utilizando vulnerabilidades conocidas: Eir D1000, Vacron NVR, dispositivos que usan Realtek SDK, Netgear R7000 y R6400, MVPower DVR, Huawei HG532, dispositivos D-Link, enrutadores GPON, CCTV DVR.

  
Fuente: [https://xakep.ru/2019/12/27/mozi/](https://xakep.ru/2019/12/27/mozi/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)