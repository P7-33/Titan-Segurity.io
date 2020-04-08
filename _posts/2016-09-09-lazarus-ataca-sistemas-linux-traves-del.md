---
title: 'Lazarus ataca sistemas Linux a través del troyano Dacls'
date: 2019-12-18T14:31:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-hLHmZUbkN1w/XfoqMMn_FlI/AAAAAAAALgE/_rno7o2YiHMNyIEqdGpOrsOcEq-v0degACLcBGAsYHQ/s640/virus-1889372_960_720.webp)](https://1.bp.blogspot.com/-hLHmZUbkN1w/XfoqMMn_FlI/AAAAAAAALgE/_rno7o2YiHMNyIEqdGpOrsOcEq-v0degACLcBGAsYHQ/s1600/virus-1889372_960_720.webp)

  

El troyano puede infectar máquinas con Windows y Linux. 

  

Lazarus, un grupo avanzado de amenazas persistentes (APT), ha ampliado su alcance con el desarrollo y uso de un troyano diseñado para atacar sistemas Linux.

  

La APT, que se sospecha que proviene de Corea del Norte, se ha conectado previamente a ataques cibernéticos mundiales y brotes de malware, incluido el infame alboroto WannaCry, el atraco a un banco de Bangladesh de 80 millones de dólares y una nueva campaña que afecta a las instituciones financieras de todo el mundo.

  

Informes recientes sugieren que Lazarus se ha convertido en un cliente de Trickbot, una empresa criminal que ofrece a los actores de amenazas patrocinados por el estado acceso a sistemas infectados junto con una colección de herramientas de piratería.

  

Lazarus puede estar dispuesto a comprar herramientas de otros pero también puede ser capaz de crear las suyas propias, como en el caso de un nuevo troyano de acceso remoto (RAT) descubierto por investigadores de Netlab 360.

  

El martes, la firma de ciberseguridad dijo que el troyano, llamado Dacls, pudo haber aparecido en la escena tan pronto como en mayo de este año, y aunque fue identificado por más de 20 proveedores de antivirus, según VirusTotal, todavía se considera "desconocido".

  

Después de investigar una muestra de malware cargada en el sitio web, el equipo determinó que era un "programa completamente funcional, encubierto y RAT para plataformas Windows y Linux" probablemente conectado a Lazarus.

  

En total, los investigadores obtuvieron cinco muestras. Una de las muestras de Windows se citó en un informe, CES Themed Targeting de Lazarus, mientras que otra muestra fue etiquetada como el trabajo de Lazarus por CyberWar. Un dominio vinculado al malware, thevagabondsatchel.com, es una indicación más de la participación de Lazarus, ya que el sitio web ha sido utilizado previamente por la APT para almacenar malware.

  

Si bien el módulo de Windows se carga dinámicamente a través de una URL remota, la variedad de Linux se compila directamente e incluye seis módulos generales para la ejecución de comandos, gestión de archivos y procesos, pruebas de acceso a la red, escaneo de red y conexiones C2.

  

Los investigadores creen que [CVE-2019-3396](https://nvd.nist.gov/vuln/detail/CVE-2019-3396), un error de ejecución remota de código que afecta a la macro Widget Connector en el servidor Atlassian Confluence versión 6.6.12 y posteriores, se utiliza para infectar sistemas e implementar Dacls.

  

El RAT, que viene en diferentes sabores según el sistema operativo al que se dirige, comparte su protocolo de comando y control (C2). Dacls es malware modular y utiliza el cifrado TLS y RC4 cuando se comunica con su C2, así como el cifrado AES para proteger los archivos de configuración.

  

Una vez que la versión de Linux aterriza en una máquina vulnerable, el malware se ejecutará en segundo plano y buscará actualizaciones. Dacls luego descomprimirá y descifrará su archivo de configuración y se conectará a su C2.

  

El troyano puede realizar funciones que incluyen robar, eliminar y ejecutar archivos; escanear estructuras de directorios, descargar cargas útiles adicionales, eliminar procesos, crear procesos de daemon y cargar datos, incluidos resultados de escaneo y salida de ejecución de comandos.

  

Como el malware se propaga a través de una vulnerabilidad conocida con un parche fácilmente disponible, se recomienda que los administradores de TI se aseguren de que sus configuraciones de Confluence se mantengan actualizadas.

  

Trend Micro descubrió otra forma interesante de malware de Linux, denominada [Skidmap](https://www.zdnet.com/article/skidmap-malware-buries-into-the-kernel-to-hide-cryptocurrency-mining/), en septiembre. El código malicioso usa rootkits en un intento de enterrarse en el núcleo y permanecer discreto mientras despliega mineros de criptomonedas ilícitos.  
  
  

Fuente: [https://www.zdnet.com/](https://www.zdnet.com/article/lazarus-pivots-to-linux-attacks-through-dacls-trojan/)

No olvides Compartir... 

  
Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)