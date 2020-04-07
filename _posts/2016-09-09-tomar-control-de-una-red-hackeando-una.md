---
title: 'Tomar control de una red hackeando una bombilla PHILIPS HUE'
date: 2020-02-06T03:57:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-cruFkl7oFaE/Xjxlgb1-bgI/AAAAAAAALvo/p2WbKbAPnvURikYMBc9hV5ERMq1PKy_awCLcBGAsYHQ/s400/sparkler-4629347_960_720.jpg)](https://1.bp.blogspot.com/-cruFkl7oFaE/Xjxlgb1-bgI/AAAAAAAALvo/p2WbKbAPnvURikYMBc9hV5ERMq1PKy_awCLcBGAsYHQ/s1600/sparkler-4629347_960_720.jpg)

  
Una firma de **[seguridad informática](https://www.iicybersecurity.com/seguridad-informatica.html)** reportó el hallazgo de una vulnerabilidad en los dispositivos Philips Hue que, de ser explotada, permitiría a un hacker tomar control de una bombilla para encenderla o apagarla a voluntad, cambiar color de luz, intensidad de brillo, entre otras tareas. La falla es explotable de forma remota empleando sólo una laptop con transmisor de radio incluido.

Acorde al reporte, la vulnerabilidad reside en el protocolo de comunicación Zigbee, empleado en **[Philips Hue](https://noticiasseguridad.com/tecnologia/bombillas-inteligentes-philips-hue-y-lifx-pueden-ser-hackeadas-para-controlar-su-hogar-y-su-vida/)** y otros dispositivos para el hogar con conexión a Internet, como altavoces inteligentes, cerraduras, termostatos, entre otros.

Los expertos en seguridad informática encontraron una manera de desplegar un ataque de escalada de privilegios a partir del Philips Hue. Dependiendo de las habilidades de los hackers, incluso podría comprometerse toda una red local. El ataque consiste en los siguientes pasos:

*   El atacante explota la vulnerabilidad original para tomar el control de un Philips Hue
*   El usuario objetivo pierde control sobre el dispositivo afectado, que es desconectado de la red
*   El usuario busca de nuevo el Philips Hue y vuelve a agregarlo a la red
*   El Philips Hue, ahora infectado, es usado por el hacker para acceder al puente Hue
*   Desde ese punto, los hackers pueden acceder a la red e incluso a equipos de cómputo conectados

Si los hackers logran acceder a una computadora en la red, pueden instalar software malicioso, como keyloggers o alguna variante de **[ransomware](https://noticiasseguridad.com/hacking-incidentes/mas-de-mil-servidores-y-5-mil-computadoras-de-importante-compania-de-transporte-infectadas-con-ransomware/)**. Los expertos en seguridad informática reportaron en tiempo y forma estas vulnerabilidades a Signify, compañía propietaria de la marca Philips Hue, que se apresuró a lanzar un parche de seguridad, el cual ya se encuentra disponible.

Aunque la falla que permite el acceso a la red fue corregida, los expertos del Instituto Internacional de Seguridad Cibernética (IICS) señalan que, debido a que la vulnerabilidad original reside en las bombillas, no es posible corregirla con actualizaciones de software, por lo que la mitigación completa de este riesgo de seguridad requeriría del lanzamiento de una bombilla completamente nueva, no obstante, la corrección lanzada por la compañía garantiza que los hackers no logren acceder a la red a partir del ataque contra el dispositivo.

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/tecnologia/tomar-control-de-una-red-hackeando-una-bombilla-philips-hue/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)