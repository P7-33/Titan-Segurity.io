---
title: 'NextCry Ransomware apunta a servidores Linux NextCloud y permanece sin
ser detectado'
date: 2019-12-01T04:05:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-KxCcMJ4dpFI/XeR1FGrA7cI/AAAAAAAALaQ/Sdn4_RI4rtcG3g0-ocAC2fljIasxOl1pgCLcBGAsYHQ/s400/ransomware-2321665_960_720.png)](https://1.bp.blogspot.com/-KxCcMJ4dpFI/XeR1FGrA7cI/AAAAAAAALaQ/Sdn4_RI4rtcG3g0-ocAC2fljIasxOl1pgCLcBGAsYHQ/s1600/ransomware-2321665_960_720.png)

  
Se ha identificado una variante de ransomware nueva y particularmente problemática en la naturaleza. Apodado NextCry, esta cepa desagradable de ransomware cifra datos en servidores Linux NextCloud y ha logrado evadir la detección de plataformas de escaneo público y motores antivirus. Para empeorar las cosas, actualmente no hay una herramienta de descifrado gratuita disponible para las víctimas.  
  
El cazador de ransomware y creador de ID Ransomware, Michael Gillespie, señala que el ransomware NextCry, que es un script de Python compilado en un binario ELF de Linux usando pyInstaller, usa Base64 para codificar nombres de archivos, así como el contenido de archivos que ya han sido encriptados. Gillespie también ha confirmado que NextCry cifra los datos utilizando el algoritmo AES con una clave de 256 bits.  
  
La nota de rescate que reciben las víctimas de NextCry dice "" READ\_FOR\_DECRYPT "y exige 0.025 BTC para desbloquear los archivos de una víctima.  
  
Un usuario de NextCloud, xact64, compartió su experiencia con el malware en un foro de Bleeping Computer en un esfuerzo por encontrar una manera de descifrar archivos personales que habían sido bloqueados instantáneamente en un ataque de NextCry: "Me di cuenta de inmediato de que mi servidor fue pirateado y esos archivos Encriptado "Lo primero que hice fue extraer el servidor para limitar el daño que se estaba haciendo (solo el 50% de mis archivos se cifraron)". Agregó: "Tengo mi propio servidor Linux (un antiguo cliente ligero que le di una segunda vida) ) con NGINX reverse-proxy ".  
  
Esta declaración proporciona información sobre cómo los piratas informáticos pudieron acceder a su sistema. El 24 de octubre, NextCloud reveló una vulnerabilidad de ejecución remota de código (CVE-2019-11043) que ha sido explotada para comprometer los servidores con la configuración predeterminada de Nextcloud NGINX.  
  
NextCloud recomienda que los administradores actualicen sus paquetes PHP y el archivo de configuración NGINX a la última versión para protegerse contra los ataques de NextCry.  
Cómo proteger su sistema Linux del ransomware:  
  
Además de actualizar a la última versión de PHP y NGINX, aquí hay una lista de las mejores prácticas que los administradores y usuarios deben implementar para proteger sus sistemas Linux de NextCry y otras variantes emergentes de ransomware:  
 

*   Actualice su sistema con frecuencia. Configure actualizaciones automáticas siempre que sea posible.
*   Rastree avisos de seguridad y aplique parches de software tan pronto como se publiquen.
*   Crea copias de seguridad de forma regular. Esto no evitará un ataque de ransomware, pero puede reducir la devastación causada por uno. Tenga en cuenta que las copias de seguridad no son infalibles: el ransomware puede permanecer inactivo durante semanas hasta que se active, lo que podría destruir las copias de seguridad.
*   El ransomware a menudo llega por correo electrónico, y los correos electrónicos de ransomware pueden ser muy difíciles de identificar. Tener una puerta de enlace de seguridad de correo electrónico de varias capas bien diseñada que detecte los correos electrónicos maliciosos (como los que contienen ransomware) y evite que lleguen a la bandeja de entrada puede disminuir significativamente el riesgo de sufrir un ataque de ransomware.

  

Fuente: [https://linuxsecurity.com/](https://linuxsecurity.com/features/features/nextcry-ransomware-targets-nextcloud-linux-servers-and-remains-undetected)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)