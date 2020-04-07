---
title: 'Ryuk Ransomware utiliza Wake-on-Lan para cifrar dispositivos sin
conexión'
date: 2020-01-15T16:17:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Ef0JrvfSL0E/Xh3Lu5jT2_I/AAAAAAAALoA/WhluKii_e-0GNA9xhz0HEd06VYLD70WUQCLcBGAsYHQ/s640/Ryuk.png)](https://1.bp.blogspot.com/-Ef0JrvfSL0E/Xh3Lu5jT2_I/AAAAAAAALoA/WhluKii_e-0GNA9xhz0HEd06VYLD70WUQCLcBGAsYHQ/s1600/Ryuk.png)

  

  

El Ryuk Ransomware utiliza la función Wake-on-Lan para encender dispositivos apagados en una red comprometida para tener un mayor éxito al encriptarlos.

  

Wake-on-Lan es una función de hardware que permite que un dispositivo apagado se active o se encienda enviando un paquete de red especial. Esto es útil para los administradores que pueden necesitar enviar actualizaciones a una computadora o realizar tareas programadas cuando se apaga.

  

Según un análisis reciente del Ryuk Ransomware del Jefe de SentinelLabs Vitali Kremez, cuando se ejecuta el malware, generará subprocesos con el argumento '8 LAN'.

  

[![](https://1.bp.blogspot.com/-nDzR54woSz0/Xh3L1rovgNI/AAAAAAAALoE/CFFjhUJ4e0c1m_bEpMNkyIm1mpR5vlB0ACLcBGAsYHQ/s640/1.jpg)](https://1.bp.blogspot.com/-nDzR54woSz0/Xh3L1rovgNI/AAAAAAAALoE/CFFjhUJ4e0c1m_bEpMNkyIm1mpR5vlB0ACLcBGAsYHQ/s1600/1.jpg)

  

Subproceso que dispersa con argumento de 8 Lan

  

Cuando se utiliza este argumento, Ryuk escaneará la tabla ARP del dispositivo, que es una lista de direcciones IP conocidas en la red y sus direcciones mac asociadas, y verificará si las entradas son parte de las subredes de direcciones IP privadas de "10." "172.16." Y "192.168".

  

[![](https://1.bp.blogspot.com/-NpEMxvYGDD0/Xh3L6A_lHRI/AAAAAAAALoI/uNIgq1O8FkkuQINXmeJ1ocrTk17xcSFswCLcBGAsYHQ/s640/2.jpg)](https://1.bp.blogspot.com/-NpEMxvYGDD0/Xh3L6A_lHRI/AAAAAAAALoI/uNIgq1O8FkkuQINXmeJ1ocrTk17xcSFswCLcBGAsYHQ/s1600/2.jpg)

  

Comprobando la red privada

  

Si la entrada ARP es parte de alguna de esas redes, Ryuk enviará un paquete Wake-on-Lan (WoL) a la dirección MAC del dispositivo para que se encienda. Esta solicitud WoL viene en forma de un 'paquete mágico' que contiene 'FF FF FF FF FF FF FF FF'.

  

[![](https://1.bp.blogspot.com/-8r3Mk-6pOT8/Xh3L-r_3ebI/AAAAAAAALoQ/hj97OxD-iMoD83xPhT9TsZjHQhPTOkH0ACLcBGAsYHQ/s640/3.jpg)](https://1.bp.blogspot.com/-8r3Mk-6pOT8/Xh3L-r_3ebI/AAAAAAAALoQ/hj97OxD-iMoD83xPhT9TsZjHQhPTOkH0ACLcBGAsYHQ/s1600/3.jpg)

  

Ryuk enviando un paquete WoL

  

Si la solicitud de WoL fue exitosa, Ryuk intentará montar el recurso compartido administrativo C $ del dispositivo remoto.

  

[![](https://1.bp.blogspot.com/-qWTtsjqJFP0/Xh3MEzL4_JI/AAAAAAAALoY/8R7DmtpvARklnI6DYIL3-r1XN_Uvg1o8gCLcBGAsYHQ/s640/5.jpg)](https://1.bp.blogspot.com/-qWTtsjqJFP0/Xh3MEzL4_JI/AAAAAAAALoY/8R7DmtpvARklnI6DYIL3-r1XN_Uvg1o8gCLcBGAsYHQ/s1600/5.jpg)

  

Montar el control remoto C $ Share

  

**Montar el control remoto C $ Share**

  

Si pueden montar el recurso compartido, Ryuk también cifrará el disco de esa computadora remota.

  

En conversaciones con BleepingComputer, Kremez declaró que esta evolución en las tácticas de Ryuk permite un mejor alcance en una red comprometida desde un solo dispositivo y muestra la habilidad del operador de Ryuk atravesando una red corporativa.

  

"Así es como el grupo adaptó el modelo de ransomware en toda la red para afectar a más máquinas a través de una sola infección y al llegar a las máquinas a través de WOL & ARP", dijo Kremez a BleepingComputer. "Permite un mayor alcance y menos aislamiento y demuestra su experiencia en grandes entornos corporativos".

  

Para mitigar esta nueva característica, los administradores solo deben permitir paquetes Wake-on-Lan desde dispositivos administrativos y estaciones de trabajo.

  

Esto permitiría a los administradores seguir beneficiándose de esta función al tiempo que agrega seguridad a los puntos finales.

  

Al mismo tiempo, esto no ayuda si una estación de trabajo administrativa se ve comprometida, lo que ocurre con bastante frecuencia en ataques de ransomware dirigidos.

  
  

Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/ryuk-ransomware-uses-wake-on-lan-to-encrypt-offline-devices/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)