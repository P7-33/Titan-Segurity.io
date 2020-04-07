---
title: 'Linux 5.6 llegara con WireGuard VPN y extensión MPTCP'
date: 2020-02-02T03:15:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-W9Kkrxdfi60/XjYwULZhLPI/AAAAAAAALuk/8Zdm7C5DEw01X15J9w0bIEb-utOybwkzgCLcBGAsYHQ/s640/wireguard.png)](https://1.bp.blogspot.com/-W9Kkrxdfi60/XjYwULZhLPI/AAAAAAAALuk/8Zdm7C5DEw01X15J9w0bIEb-utOybwkzgCLcBGAsYHQ/s1600/wireguard.png)

  

El mes pasado, **David S. Miller (******responsable del subsistema de red en Linux**),** dio a conocer la noticia que en la cual tomo parches con** la implementación de la interfaz VPN del proyecto WireGuard en la rama net-next.**

  

Con ello **Linus Torvalds se hizo cargo del repositorio,** que forma la futura rama del kernel de Linux 5.6 y después de algunos cambios alrededor de la 1 am CET del miércoles, Torvalds sacó las actualizaciones de redes del repositorio de David Millers, con WireGuard en la parte superior de la lista.

  

Con ello **el kernel de Linux 5.6 esperado** a fines de marzo o principios de abril **finalmente admitirá la tecnología de túnel VPN WireGuard**, así como también el soporte inicial para la extensión MPTCP (MultiPath TCP).

  

Anteriormente, las primitivas criptográficas necesarias para que WireGuard funcionara se transfirieron de la biblioteca Zinc a la API Crypto estándar y se incluyeron en el núcleo 5.5.

  

El kernel de **Linux probablemente habría brindado soporte de Wireguard durante mucho tiempo,** si no hubiera habido una disputa sobre la base de cifrado desarrollada específicamente para la tecnología VPN. Tomó alrededor de un año y medio resolver estas inconsistencias.

  

Este proceso se derivó que **el equipo de trabajo de WireGuard tomara cartas en el asunto,** ya que después de las negociaciones **en la conferencia Kernel Recipes,** en la cual los creadores de WireGuard **en septiembre tomaron una decisión de compromiso de cambiar sus parches** para usar la API Crypto core, de la cual los desarrolladores de WireGuard tienen quejas en términos de rendimiento y seguridad general.

  

Se decidió que la API continuara desarrollándose, pero como un proyecto separado. **Posteriormente en noviembre, los desarrolladores del kernel hicieron un compromiso** y acordaron transferir parte del código al kernel principal. De hecho, algunos componentes se transferirán al kernel, pero no como una API separada, sino como parte del subsistema Crypto API.

  

**Wireguard promete un establecimiento de conexión rápido, un buen rendimiento,** así como un manejo robusto, rápido y transparente de abortos de conexión. Además, la tecnología es mucho más fácil de configurar que otras tecnologías VPN e implementa la seguridad contra las escuchas con los últimos algoritmos de cifrado.

  

En su sitio web, el equipo de WireGuard explica qué diferencia a su protocolo de los demás y dice:

  

> _“WireGuard ha sido diseñado teniendo en cuenta la facilidad de implementación y la simplicidad._  
> _Está destinado a implementarse fácilmente en muy pocas líneas de código, y fácilmente auditable por vulnerabilidades de seguridad._  
> _En comparación con gigantes como \* Swan / IPsec u OpenVPN / OpenSSL, en los que auditar las bases de código gigantescas es una tarea abrumadora incluso para grandes equipos de expertos en seguridad, WireGuard está destinado a ser revisado de forma exhaustiva por personas individuales “._

**Multipath TCP,** por otro lado, **es una extensión del protocolo TCP que permite organizar la operación de una conexión TCP** con entrega de paquetes simultáneamente en varias rutas a través de diferentes interfaces de red que están vinculadas a diferentes direcciones IP (el uso de varias conexiones de datos al mismo tiempo)

  

Multipath TCP **se puede utilizar tanto para ampliar el rendimiento como para aumentar la fiabilidad**.

  

Por ejemplo, MPTCP se puede usar para organizar la transferencia de datos en un teléfono inteligente usando enlaces WiFi y 3G al mismo tiempo, o para reducir costos conectando un servidor usando varios enlaces baratos en lugar de uno costoso.

  

Otro caso, por ejemplo, es con los servidores apropiados, puede ocurrir un cambio ininterrumpido de WLAN a conexiones de teléfonos celulares si se excede el rango de WLAN. Integrar Multipath TCP en Linux también es ventajoso porque la próxima tecnología móvil 5G requiere la tecnología.

  

Finalmente, **se espera que la nueva versión del Kernel de Linux 5.6** tal y como mencionamos al principio **llegue** a finales de marzo (una fecha tentativa es **el 29 de marzo**) o a principios de abril (**6 de abril**) aunque esto puede variar un poco.  
  

Fuente: [https://www.linuxadictos.com/](https://www.linuxadictos.com/linux-5-6-llegara-con-wireguard-vpn-y-extension-mptcp.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)