---
title: 'Las vulnerabilidades en SQLite permiten la ejecución remota de código
en Chrome'
date: 2020-01-05T02:04:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-AmODG7Lg1Sg/XhE2RoGTDvI/AAAAAAAALks/_K4eAGcD2wEwaAU4nHt9PLDF9NNW3nAuACLcBGAsYHQ/s640/Magellan2-384x220.jpg)](https://1.bp.blogspot.com/-AmODG7Lg1Sg/XhE2RoGTDvI/AAAAAAAALks/_K4eAGcD2wEwaAU4nHt9PLDF9NNW3nAuACLcBGAsYHQ/s1600/Magellan2-384x220.jpg)

  
Los expertos de Tencent Blade informaron que se descubrieron cinco nuevas vulnerabilidades en SQLite, denominadas colectivamente [Magellan 2.0](https://blade.tencent.com/magellan2/index_en.html) (CVE-2019-13734, CVE-2019-13750, CVE-2019-13751, CVE-2019-13752 y CVE-2019-13753). Le permiten ejecutar código arbitrario de forma remota en el navegador Chrome, y también provocan una pérdida de memoria o un bloqueo en el programa.

El problema es peligroso para cualquier aplicación que use SQLite, pero los riesgos para los usuarios de Chrome son mayores debido a la API de WebSQL, que pone a los usuarios en riesgo de ataques remotos. Los usuarios de Opera también enfrentan riesgos similares.

Permítanme recordarles que hace un año, en diciembre de 2018, los mismos especialistas descubrieron problemas peligrosos en SQLite, que se llamaron [Magellan](https://xakep.ru/2018/12/17/magellan/) (CVE-2018-20346, CVE-2018-20505 y CVE-2018-20506). Los errores permitidos para ejecutar código arbitrario, condujeron a una pérdida de memoria de programas, "bloqueos" de aplicaciones y en total amenazaron a miles de productos móviles y de escritorio. Dado que SQLite se puede encontrar en una amplia variedad de soluciones, el problema afectó a dispositivos IoT, software de escritorio, navegadores y aplicaciones para iOS y Android.

Ahora, los investigadores de Tencent Blade han hablado sobre nuevos errores que también están asociados con una validación de entrada incorrecta en los comandos SQL que la base de datos SQLite recibe de terceros. Como resultado, para explotar el problema, el atacante solo necesita crear una operación SQL que contenga código malicioso. Es decir, un sitio malicioso puede usar Magellan 2.0 para ejecutar código malicioso en los navegadores de sus visitantes.

Afortunadamente, los investigadores informan que los desarrolladores de Chrome ya han solucionado todos los errores de Magellan 2.0 con el lanzamiento de Chrome 79.0.3945.79, que tuvo lugar hace dos semanas. Los desarrolladores de SQLite también [corrigieron errores](https://www.sqlite.org/src/timeline) desde el 13 de diciembre de 2019, pero estos parches aún no se han incluido en la rama estable de SQLite (3.30.1, lanzado el 10 de diciembre de 2019, sigue siendo la versión más reciente).

Los expertos de Tencent Blade enfatizan que no son conscientes de la existencia de exploits para los problemas detectados, ni de los casos de ataques a estas vulnerabilidades. En un futuro cercano, los investigadores tienen la intención de publicar información más detallada sobre las vulnerabilidades, pero hasta ahora se han limitado a un resumen de sus hallazgos, dando a los desarrolladores de aplicaciones la oportunidad de actualizar.

  
  
Fuente: [https://xakep.ru/](https://xakep.ru/2019/12/25/magellan-2-0/)  

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)