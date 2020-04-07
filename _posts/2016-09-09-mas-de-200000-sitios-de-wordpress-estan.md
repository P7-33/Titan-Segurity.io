---
title: 'Más de 200,000 sitios de WordPress están en riesgo debido a la
vulnerabilidad de fragmentos de código'
date: 2020-02-03T16:00:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-vZnj4OR2cco/Xjg06nEx20I/AAAAAAAALvA/GhCA4Zzc8bckUTd1KiJWwjDglNarbhniQCLcBGAsYHQ/s640/Code-Snippets-384x220.png)](https://1.bp.blogspot.com/-vZnj4OR2cco/Xjg06nEx20I/AAAAAAAALvA/GhCA4Zzc8bckUTd1KiJWwjDglNarbhniQCLcBGAsYHQ/s1600/Code-Snippets-384x220.png)

Los expertos de Wordfence [encontraron una](https://translate.googleusercontent.com/translate_c?depth=1&hl=ru&rurl=translate.google.com&sl=en&sp=nmt4&tl=ru&u=https://www.wordfence.com/blog/2020/01/high-severity-csrf-to-rce-vulnerability-patched-in-code-snippets-plugin/&xid=17259,15700022,15700186,15) peligrosa vulnerabilidad CSRF ( [CVE-2020-8417](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-8417) ) como parte del popular plugin Code Snippets diseñado para WordPress. Esencialmente, un error permite que un atacante tome el control completo de un recurso vulnerable.

Según [las estadísticas oficiales de](https://wordpress.org/plugins/code-snippets/) WordPress, los fragmentos de código de código abierto se han instalado en más de 200,000 sitios. El complemento está diseñado para ejecutar fragmentos para sitios PHP WordPress, y también proporciona una GUI conveniente para administrarlos, similar al menú Complementos.

La vulnerabilidad permitió a los atacantes falsificar solicitudes como administrador e inyectar código en sitios vulnerables, lo que finalmente llevó a la ejecución remota de código arbitrario en sitios con versiones vulnerables de fragmentos de código. El atacante pudo crear una nueva cuenta de administrador, obtuvo acceso a datos confidenciales, pudo atacar a los visitantes del recurso, etc.

Los investigadores dicen que, en general, el desarrollador del complemento pensó en la seguridad bastante bien, protegiendo casi todos los puntos finales con WordPress nonces, pero la función de importación no tenía esa protección contra CSRF. Por lo tanto, el atacante podría obligar al administrador a infectar su propio sitio utilizando una solicitud maliciosa especialmente preparada.

CSRF-RCE ahora se ha solucionado con el lanzamiento de Code Snippets versión 2.14.0. A juzgar por las estadísticas oficiales, aproximadamente 58,000 usuarios ya han descargado e instalado la última versión del complemento, lo que significa que al menos 140,000 sitios aún son vulnerables a los ataques. 

[![](https://xakep.ru/wp-content/uploads/2020/01/267223/Code-Snippets-download-history.png#26759185)](https://xakep.ru/wp-content/uploads/2020/01/267223/Code-Snippets-download-history.png#26759185)

Un video que demuestra un ataque de PoC se puede ver a continuación. Los investigadores prometieron publicar el exploit el 12 de febrero, que desean dar a los usuarios de complementos más tiempo para instalar actualizaciones.

  

Fuente: [https://xakep.ru/](https://xakep.ru/2020/01/31/code-snippets/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)