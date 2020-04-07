---
title: 'Enfold v4.7.1 – Responsive Multi-Purpose Theme'
date: 2020-01-15T14:34:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-zPx0X2sRqWo/Xh8Vnx5kblI/AAAAAAAALow/eT_soqgtL80dRbFXndEykSZ8dA8n4xp_wCLcBGAsYHQ/s640/Vulnerabilidad-grave-en-Criptograf%25C3%25ADa-de-Windows-10.jpg)](https://1.bp.blogspot.com/-zPx0X2sRqWo/Xh8Vnx5kblI/AAAAAAAALow/eT_soqgtL80dRbFXndEykSZ8dA8n4xp_wCLcBGAsYHQ/s1600/Vulnerabilidad-grave-en-Criptograf%25C3%25ADa-de-Windows-10.jpg)

  
Según [KrebsOnSecurity](https://krebsonsecurity.com/2020/01/cryptic-rumblings-ahead-of-first-2020-patch-tuesday/) , [Microsoft](https://www.secureweek.com/windows-7-vs-windows-10-cual-es-mejor/) Corp lanzó una actualización de software el martes 14 de Enero para corregir una vulnerabilidad de [seguridad](https://www.secureweek.com/) extraordinariamente grave en un componente criptográfico central presente en todas las versiones de [Windows](https://www.secureweek.com/guia-de-seguridad-de-windows-10/) . Esas fuentes dicen que Microsoft ha enviado silenciosamente un parche para el error a las ramas del ejército de los EE. UU. Y a otros clientes / objetivos de alto valor que administran la infraestructura clave de Internet, y que a esas organizaciones se les ha pedido que firmen acuerdos que les impiden revelar detalles del falla antes del 14 de enero, el primer parche martes de 2020.

Según las fuentes, la vulnerabilidad en cuestión reside en un componente de [Windows](https://www.secureweek.com/windows-7-vs-windows-10-cual-es-mejor/) conocido como [crypt32.dll](https://docs.microsoft.com/en-us/windows/win32/seccrypto/crypt32-dll-versions) , un módulo de Windows que Microsoft dice que maneja «funciones de certificado y mensajería criptográfica en CryptoAPI». [Microsoft CryptoAPI](https://en.wikipedia.org/wiki/Microsoft_CryptoAPI)  proporciona servicios que permiten a los desarrolladores proteger Windows aplicaciones que usan criptografía e incluye funcionalidad para encriptar y desencriptar datos usando certificados digitales.

Una vulnerabilidad crítica en este componente de Windows podría tener implicaciones de seguridad de gran alcance para una serie de funciones importantes de Windows, incluida la autenticación en los escritorios y servidores de Windows, la protección de datos confidenciales manejados por los navegadores Internet Explorer / Edge de Microsoft, así como una serie de Aplicaciones y herramientas de terceros.

Igualmente preocupante, una falla en crypt32.dll _también puede ser abusada para falsificar la firma digital vinculada a una pieza específica de software_ . Los atacantes podrían aprovechar esa debilidad para hacer que el malware parezca un programa benigno producido y firmado por una compañía de software legítima.

El CryptoAPI es lo que permite a los desarrolladores asegurar aplicaciones basadas en Windows y cualquier vulnerabilidad crítica aquí podría afectar el cifrado y descifrado mediante certificados digitales. Krebs dijo que también podría afectar la «autenticación en los escritorios y servidores de Windows, la protección de datos confidenciales manejados por los navegadores Internet Explorer / Edge de Microsoft, así como una serie de aplicaciones y herramientas de terceros».

¿Qué implica esta vulnerabilidad para la seguridad de Windows?
--------------------------------------------------------------

En este punto, debe reiterarse que esto sigue siendo una conjetura, no se ha hecho ninguna revelación y ni Microsoft ni la NSA están diciendo nada más allá de confirmar que los detalles de cualquier vulnerabilidad no serán discutidos antes de que una actualización esté disponible.

«Si es cierto que hay [vulnerabilidades](https://www.secureweek.com/vulnerabilidad-en-camara-ip-amcrest-ip2m-841b-basada-en-codigo-de-dahua/) en CryptoAPI de Microsoft», dice el profesional de seguridad [John Opdenakker](https://twitter.com/j_opdenakker "https://twitter.com/j_opdenakker") , «el impacto potencial puede ser grande. Desde el pasado, también sabemos que muchas empresas y personas no se apresuran a parchar, lo que los pone en riesgo. Esto muestra por qué las actualizaciones automáticas son tan importantes «.

«Si la solución ya ha sido enviada a organizaciones como el ejército de Estados Unidos» , dice [Sean Wright](https://twitter.com/SeanWrightSec "https://twitter.com/SeanWrightSec") , líder del capítulo en OWASP Escocia, «respalda aún más esta sospecha. Va a ser realmente interesante ver qué es».

Esperemos la actualización de Microsoft [Windows 10](https://www.secureweek.com/una-revision-de-microsoft-windows-10/) que ha sido programada para ayer para conocer más detalles. Por lo pronto si desea obtener mayor información, dirijase a el articulo de KrebsonSecurity : [https://krebsonsecurity.com/2020/01/cryptic-rumblings-ahead-of-first-2020-patch-tuesday/](https://krebsonsecurity.com/2020/01/cryptic-rumblings-ahead-of-first-2020-patch-tuesday/)  
  
  

Fuente: [https://www.secureweek.com/](https://www.secureweek.com/vulnerabilidad-grave-en-criptografia-de-windows-10/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)