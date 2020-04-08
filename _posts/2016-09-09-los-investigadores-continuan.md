---
title: 'Los investigadores continúan descubriendo similitudes entre los
criptógrafos GandCrab y Sodinokibi'
date: 2019-09-25T23:15:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-W-ZzYY9r3y0/XYvm4zOC5lI/AAAAAAAALBQ/A1ZkNCUOn1QLLBEGGy2wzPWSPgkdpF5CQCLcBGAsYHQ/s640/33433853466_4d625b4aef_b.jpg)](https://1.bp.blogspot.com/-W-ZzYY9r3y0/XYvm4zOC5lI/AAAAAAAALBQ/A1ZkNCUOn1QLLBEGGy2wzPWSPgkdpF5CQCLcBGAsYHQ/s1600/33433853466_4d625b4aef_b.jpg)

  
A principios del verano de este año, los operadores de ransomware GandCrab [anunciaron](https://xakep.ru/2019/06/03/gandcrab-shutting-down/) la finalización de la actividad, ya que ya han ganado lo suficiente. Sin embargo, los expertos de SecureWorks [creen](https://www.secureworks.com/research/revil-sodinokibi-ransomware) que GandCrab dejó un "heredero" detrás de sí mismo: después de examinar el código de ransomware REvil (también conocido como Sodinokibi), que apareció casi simultáneamente con la "renuncia" de GandCrab, los investigadores sugirieron que el ransomware estaba conectado.

La conexión probable entre las dos amenazas se ha escrito durante mucho tiempo. Por ejemplo, cuando Sodinokibi atacó los servidores de WebLogic, los expertos de Cisco [notaron](https://blog.talosintelligence.com/2019/04/sodinokibi-ransomware-exploits-weblogic.html) que los mismos atacantes pronto enviaron a los hosts infectados y GandCrab 5.2. Incluso entonces, muchos expertos sugirieron que el nuevo malvar era de hecho el sucesor del antiguo y, aparentemente, no se equivocaron.

Los analistas de SecureWorks escriben que definitivamente hay una conexión entre los dos malware. Entonces, la versión beta de Sodinokibi se subió a VirusTotal el 10 de abril de 2019, y la primera versión estable con la construcción de URI, igual que GandCrab, apareció veinte días después.

[![](https://xakep.ru/wp-content/uploads/2019/09/240246/REvil-activity-Secureworks.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/09/240246/REvil-activity-Secureworks.jpg#26759185)

Al examinar estas primeras versiones de Sodinokibi, los investigadores encontraron que el ransomware usaba casi las mismas funciones de decodificación de cadenas GandCrab. Continuando con el análisis del código, los especialistas buscaron otras muestras adecuadas en VirusTotal y llegaron a la conclusión de que solo GandCrab, Sodinokibi o descifradores para ellos muestran coincidencias.

[![](https://xakep.ru/wp-content/uploads/2019/09/240246/shared-code.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/09/240246/shared-code.jpg#26759185)[![](https://xakep.ru/wp-content/uploads/2019/09/240246/REvil-decodefcn-Secureworks.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/09/240246/REvil-decodefcn-Secureworks.jpg#26759185)

También en el código de Sodinokibi, fue posible identificar artefactos, aparentemente, que quedan de GandCrab allí: por ejemplo, el nombre del proyecto es gcfin, que, según los investigadores, significa "GandCrab Final" o gc6, que significa "GandCrab 6".

Si bien los expertos no pueden decirlo con certeza, las mismas personas están detrás de Sodinokbi y GandCrab, o el grupo GandCrab realmente se retiró, y los desarrolladores de Malvari ahora están colaborando con otros delincuentes. También es posible que los operadores de GandCrab generalmente vendieran su "negocio" a otros delincuentes y Sodinokibi ya estaba haciendo su trabajo.  
  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2019/09/25/sodinokibi-gandcrab/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)