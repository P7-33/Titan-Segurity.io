---
title: 'El paquete npm malicioso roba datos de sistemas UNIX'
date: 2020-01-14T15:04:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-kVVzlDl8Hq8/Xh3KVlg4g4I/AAAAAAAALnw/qOjOXfACz1EwqNLI_aTYuXRTWAz2VGwSQCLcBGAsYHQ/s640/malware-384x220.jpg)](https://1.bp.blogspot.com/-kVVzlDl8Hq8/Xh3KVlg4g4I/AAAAAAAALnw/qOjOXfACz1EwqNLI_aTYuXRTWAz2VGwSQCLcBGAsYHQ/s1600/malware-384x220.jpg)

El equipo de seguridad del popular administrador de paquetes JavaScript npm (Node Package Manager) descubrió el paquete malicioso [1337qq-js](https://www.npmjs.com/package/1337qq-js) que [robó](https://www.npmjs.com/package/1337qq-js) datos confidenciales de los sistemas UNIX. Este es el sexto caso desde 2017, cuando el malware ingresó al repositorio npm.

El paquete malicioso se cargó en el repositorio el 30 de diciembre de 2019, lograron descargarlo al menos 32 veces, y luego lo notaron los especialistas en seguridad de la información de Microsoft. Según el análisis de los investigadores, el paquete roba información confidencial mediante scripts de instalación y está diseñado exclusivamente para sistemas UNIX. Entre los datos robados:

*   variables de entorno
*   procesos en ejecución;
*   / etc / hosts;
*   uname -a;
*   archivo npmrc

Cabe señalar que el robo de variables de entorno es muy peligroso, ya que las contraseñas codificadas y los tokens de acceso API en aplicaciones web y móviles a menudo se almacenan en forma de variables de entorno.

Ahora, todos los desarrolladores que lograron descargar un paquete peligroso, se recomienda eliminarlo urgentemente de sus sistemas y cambiar todas las credenciales comprometidas.

  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2020/01/14/npm-malware/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)