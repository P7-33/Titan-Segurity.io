---
title: 'La nueva vulnerabilidad de Linux permite a los atacantes secuestrar
conexiones VPN'
date: 2019-12-07T01:22:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-xmNG-6WUM8Y/Xe2ouMTN8EI/AAAAAAAALcU/c6e9LLxoCa4r_ZZSyy--8NPQaL7fPCdYACLcBGAsYHQ/s640/Linux_Malware.webp)](https://1.bp.blogspot.com/-xmNG-6WUM8Y/Xe2ouMTN8EI/AAAAAAAALcU/c6e9LLxoCa4r_ZZSyy--8NPQaL7fPCdYACLcBGAsYHQ/s1600/Linux_Malware.webp)

  
Los investigadores de seguridad encontraron una nueva vulnerabilidad que permite a los atacantes potenciales secuestrar las conexiones VPN en los dispositivos \* NIX afectados e inyectar cargas de datos arbitrarias en flujos TCP IPv4 e IPv6.  
  
Revelaron la falla de seguridad rastreada como CVE-2019-14899 a las distribuciones y al equipo de seguridad del kernel de Linux, así como a otras personas afectadas como Systemd, Google, Apple, OpenVPN y WireGuard.  
  
Se sabe que la vulnerabilidad afecta la mayoría de las distribuciones de Linux y los sistemas operativos tipo Unix, incluidos FreeBSD, OpenBSD, macOS, iOS y Android.  
  
A continuación, se encuentra disponible una lista incompleta de los sistemas operativos vulnerables y los sistemas init con los que vinieron, y se agregarán más una vez que se prueben y se descubra que están afectados:  
  
• Ubuntu 19.10 (systemd)  
• Fedora (systemd)  
• Debian 10.2 (systemd)  
• Arco 2019.05 (systemd)  
• Manjaro 18.1.1 (systemd)  
• Devuan (sysV init)  
• MX Linux 19 (Mepis + antiX)  
• Linux vacío (runit)  
• Slackware 14.2 (rc.d)  
• Deepin (rc.d)  
• FreeBSD (rc.d)  
• OpenBSD (rc.d)  
Todas las implementaciones de VPN se ven afectadas  
  
Esta falla de seguridad "permite que un atacante adyacente de la red determine si otro usuario está conectado a una VPN, la dirección IP virtual que les ha asignado el servidor VPN y si existe o no una conexión activa a un sitio web determinado", según William J. Tolley, Beau Kujath y Jedidiah R. Crandall, investigadores de Breakpointing Bad de la Universidad de Nuevo México.  
  
"Además, podemos determinar los números exactos de seq y ack contando los paquetes cifrados y / o examinando su tamaño. Esto nos permite inyectar datos en el flujo TCP y secuestrar conexiones", dijeron los investigadores.  
  
Los ataques que explotan CVE-2019-14899 funcionan contra OpenVPN, WireGuard e IKEv2 / IPSec, pero los investigadores aún están probando su viabilidad contra Tor.  
  
También señalan que la tecnología VPN utilizada no parece ser importante ya que los ataques funcionaron durante sus pruebas, incluso cuando las respuestas que obtuvieron de los objetivos estaban encriptadas, dado que el tamaño de los paquetes y la cantidad de paquetes enviados fueron suficientes para encontrar El tipo de paquetes de datos que se entregaron a través del túnel VPN cifrado.  
  
Este ataque no funcionó contra ninguna distribución de Linux que probamos hasta el lanzamiento de Ubuntu 19.10, y notamos que la configuración de rp\_filter estaba configurada en modo "flojo". Vemos que la configuración predeterminada en sysctl.d / 50-default.conf en el repositorio systemd se cambió de modo "estricto" a "suelto" el 28 de noviembre de 2018, por lo que las distribuciones que usan una versión de systemd sin configuraciones modificadas después de esta fecha ahora son vulnerables La mayoría de las distribuciones de Linux que probamos que usan otros sistemas de inicio dejan el valor como 0, el valor predeterminado para el kernel de Linux.  
  
Los investigadores descubrieron que la mayoría de las distribuciones de Linux que probaron eran vulnerables a los ataques que explotaban esta falla. También descubrieron que todas las distribuciones que usan versiones de systemd lanzadas después del 28 de noviembre de 2018, que vienen con el filtro Reverse Path cambiado del modo Strict al modo Loose, son vulnerables.  
  
Dado esto, todas las distribuciones de Linux que usan una versión systemd con configuraciones predeterminadas después de esta fecha son vulnerables.  
  
Sin embargo, es importante tener en cuenta que, a pesar de que algunas distribuciones con versiones específicas de systemd son vulnerables, se sabe que la falla afecta a una variedad de sistemas init y no solo está relacionada con systemd como se muestra en la lista de sistemas operativos afectados disponibles anteriormente.  
  
Además, el consultor de seguridad de red Noel Kuntze dijo en una respuesta al informe de divulgación que solo las implementaciones de VPN basadas en rutas se ven afectadas por esta vulnerabilidad.  
  
Un supuesto empleado de Amazon Web Services también declaró que la distribución de Amazon Linux y los productos de AWS VPN no se ven afectados por los ataques que explotan esta falla.  
La mitigación es posible  
  
Según los investigadores, la mitigación es posible y se puede lograr activando el filtrado de ruta inversa, mediante el uso de filtrado de bogon (filtrado de direcciones IP falsas (falsas)) o con la ayuda del tamaño y el tiempo de paquetes cifrados.  
  
Estos son los pasos necesarios para ejecutar un ataque diseñado para aprovechar esta vulnerabilidad y secuestrar la conexión VPN de un objetivo:  
  
1\. Determinar la dirección IP virtual del cliente VPN  
2\. Usando la dirección IP virtual para hacer inferencias sobre conexiones activas  
3\. Usando las respuestas encriptadas a paquetes no solicitados para determinar la secuencia y los números de reconocimiento de la conexión activa para secuestrar la sesión TCP  
  
El procedimiento completo para reproducir la vulnerabilidad en las distribuciones de Linux se explica en detalle en el informe de divulgación disponible públicamente aquí.  
  
El equipo de investigación planea publicar un documento con un análisis en profundidad de esta vulnerabilidad y sus implicaciones, pero solo después de encontrar una solución adecuada.  
  
Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/new-linux-vulnerability-lets-attackers-hijack-vpn-connections/)  

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)