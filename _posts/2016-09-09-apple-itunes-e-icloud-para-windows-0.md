---
title: 'Apple iTunes e iCloud para Windows 0-Day explotados en ataques de
ransomware'
date: 2019-10-11T20:48:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-7u0pGfmdMkU/XaDblC-mRfI/AAAAAAAALGo/_ovr9bn67jc0kE8UIoRuqiHqozl9D6DrwCLcBGAsYHQ/s640/apple-Bonjour-ransomware.jpg)](https://1.bp.blogspot.com/-7u0pGfmdMkU/XaDblC-mRfI/AAAAAAAALGo/_ovr9bn67jc0kE8UIoRuqiHqozl9D6DrwCLcBGAsYHQ/s1600/apple-Bonjour-ransomware.jpg)

  

¡Cuidado con los usuarios de Windows!

  

Se ha encontrado que el grupo cibercriminal detrás de los ataques de ransomware BitPaymer e iEncrypt explota una vulnerabilidad de día cero que afecta a un componente poco conocido que viene incluido con el software iTunes e iCloud de Apple para Windows para evadir la detección de antivirus.

  

El componente vulnerable en cuestión es el actualizador Bonjour, una implementación de configuración cero del protocolo de comunicación de red que funciona silenciosamente en segundo plano y automatiza varias tareas de red de bajo nivel, incluida la descarga automática de futuras actualizaciones para el software de Apple.

  

Cabe señalar que, dado que el actualizador Bonjour se instala como un programa separado en el sistema, la desinstalación de iTunes e iCloud no elimina Bonjour, por lo que finalmente se dejó instalado en muchas computadoras con Windows, sin actualizar y ejecutándose silenciosamente en segundo plano.

  

Investigadores de ciberseguridad de Morphisec Labs descubrieron la explotación de la vulnerabilidad de día cero de Bonjour en agosto cuando  atacaron una empresa no identificada en la industria automotriz, el ransomware BitPaymer.

  

Vulnerabilidad de ruta de servicio no citada en el servicio Bonjour de Apple

  

El componente Bonjour se consideró vulnerable a la vulnerabilidad de ruta de servicio no citada, una falla de seguridad de software común que ocurre cuando la ruta de un ejecutable contiene espacios en el nombre del archivo y no está encerrada entre comillas ("").

  

La vulnerabilidad de ruta de servicio no citada puede explotarse plantando un archivo ejecutable malicioso en la ruta principal, engañando a aplicaciones legítimas y confiables para que ejecuten programas maliciosos para mantener la persistencia y evadir la detección.

  

"En este escenario, Bonjour estaba tratando de ejecutarse desde la carpeta Archivos de programa, pero debido a la ruta sin comillas, en su lugar ejecutó el ransomware BitPaymer ya que se llamó Programa", dijeron los investigadores.

  

"Como muchas soluciones de detección se basan en la supervisión del comportamiento, la cadena de ejecución del proceso (padre-hijo) juega un papel importante en la fidelidad de la alerta. Si un proceso legítimo firmado por un proveedor conocido ejecuta un nuevo proceso hijo malicioso, una alerta asociada tendrá un puntaje de confianza más bajo que si el padre no estuviera firmado por un proveedor conocido ".

  

"Dado que Bonjour está firmado y es conocido, el adversario usa esto para su ventaja".

  

Además de escapar de la detección, en algunos casos, la vulnerabilidad de ruta de servicio no citada también podría ser abusada para escalar privilegios cuando el programa vulnerable tiene los derechos para ejecutarse con privilegios más altos.

  

Sin embargo, en este caso particular, el día cero de Bonjour no permitió que el ransomware BitPaymer obtuviera derechos de SISTEMA en las computadoras infectadas. Pero sí permitió que el malware evadiera soluciones de detección comunes que se basan en la supervisión del comportamiento porque el componente Bonjour parece un proceso legítimo.

  

Lanzamiento de parches de seguridad (iTunes / iCloud para Windows)

  

Inmediatamente después de descubrir el ataque, los investigadores de Morphisec Labs compartieron responsablemente los detalles del ataque con Apple, quien ayer lanzó iCloud para Windows 10.7, iCloud para Windows 7.14 e iTunes 12.10.1 para Windows para abordar la vulnerabilidad.

  

Se recomienda encarecidamente a los usuarios de Windows que tengan iTunes o iCloud instalado en su sistema que actualicen su software a las últimas versiones.

  

En caso de que alguna vez haya instalado uno de estos software de Apple en su computadora con Windows y luego lo haya desinstalado, debe verificar la lista de aplicaciones instaladas en su sistema para el actualizador Bonjour y desinstalarlo manualmente.  
  
  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2019/10/apple-bonjour-ransomware.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)