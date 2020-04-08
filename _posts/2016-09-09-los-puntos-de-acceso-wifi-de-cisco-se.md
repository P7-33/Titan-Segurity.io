---
title: 'Los puntos de acceso WIFI de cisco se pueden hackear fácilmente.
Desconéctelos y proteja su red.'
date: 2019-10-21T15:27:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-0euhMKsmUcs/Xa3AStJjJCI/AAAAAAAALJo/KCUHn-WE2pMo1bbXG5IV-Jrw0BPXJaVBACLcBGAsYHQ/s400/computer-158719_960_720.png)](https://1.bp.blogspot.com/-0euhMKsmUcs/Xa3AStJjJCI/AAAAAAAALJo/KCUHn-WE2pMo1bbXG5IV-Jrw0BPXJaVBACLcBGAsYHQ/s1600/computer-158719_960_720.png)

  

Acorde a expertos en **[forense digital](https://www.iicybersecurity.com/curso-forense-digital.html)**, Cisco ha emprendido una nueva jornada laboral llena de parches de seguridad para corregir múltiples vulnerabilidades críticas presentes en sus puntos de acceso inalámbricos Aironet, ampliamente utilizados por compañías pequeñas y medianas.

La compañía también lanzó parches de seguridad adicionales para corregir diversas fallas en otros de sus productos. La más severa de estas vulnerabilidades podría permitir a un hacker remoto no autenticado obtener acceso a dispositivos específicos, lo que otorga privilegios elevados, como la capacidad de acceder a datos confidenciales y modificar las configuraciones del dispositivo. Esta vulnerabilidad existe en el software de **[Cisco](https://noticiasseguridad.com/vulnerabilidades/alerta-vulnerabilidad-critica-de-acceso-raiz-en-dispositivos-cisco-actualice-de-inmediato/)** que se ejecuta en los puntos de acceso Aironet, que permiten que un dispositivo se conecte a una red con cables.

En su alerta de seguridad, la compañía mencionó: “Aunque el ataque no proporcionaría acceso a todas las opciones de configuración disponibles, el atacante sí podría acceder a información confidencial del sistema, además de modificar algunas configuraciones, como las de redes inalámbricas”.

Identificada como CVE-2019-15260, la vulnerabilidad cuenta con un puntaje de 9.8/10 en la escala del Common Vulnerability Scoring System (CVSS), lo que la convierte en una vulnerabilidad crítica. Acorde a los expertos en forense digital, la falla existe debido al débil control de acceso en determinadas URL de los dispositivos afectados.

Un actor de amenazas podría explotar la falla solicitando URL específicas de un punto de acceso afectado. Los dispositivos Aironet afectados incluyen las series 1540, 1560, 1800, 2800, 3800 y 4800.

Además de esta falla, se encontraron dos vulnerabilidades adicionales en Aironet. Una de estas vulnerabilidades existe debido a un error en una funcionalidad de procesamiento en los puntos de acceso, que procesa sólo paquetes VPN de protocolo de túnel punto a punto, un método obsoleto para implementar VPN en cualquier dispositivo. Esta falla, identificada como CVE-2019-15261, permite que un hacker remoto no autenticado desencadene la recarga de un dispositivo afectado, generando una condición de **[denegación de servicio](https://noticiasseguridad.com/hacking-incidentes/337-abusadores-de-ninos-y-hackers-de-todo-el-mundo-arrestados-un-sitio-en-deep-web-eliminado-y-ninos-salvados/)** (DoS).

La segunda vulnerabilidad, identificada como CVE-2019-15264, existe en la implementación del protocolo de “Control y Aprovisionamiento de Puntos de Acceso Inalámbrico”, de Aironet y Catalyst 9100. Este protocolo permite que cualquier controlador de acceso LAN inalámbrico central administre una colección de puntos de acceso inalámbrico. La explotación de esta vulnerabilidad permitiría que un hacker no autenticado reinicie el dispositivo de forma inadvertida, generando una condición DoS.

Los expertos en forense digital mencionan que Cisco lanzó parches de actualización para corregir un total de 41 vulnerabilidades, incluyendo la falla crítica mencionada, 17 vulnerabilidades severas y 23 fallas de gravedad menor.

Uno de los productos que más fallas de seguridad presentó es el adaptador de teléfono análogo de la serie SPA100, usado para el acceso a servicios de telefonía por Internet en cientos de pequeñas empresas. La explotación de la mayoría de estas fallas permitiría que un hacker autenticado ejecute código arbitrario.

De forma periódica, Cisco lanza parches de actualización para diversos de sus productos. Según reportaron expertos en forense digital del Instituto Internacional de Seguridad Cibernética (IICS) el mes de septiembre, la compañía lanzó 29 parches para corregir fallas de seguridad en múltiples productos, como enrutadores, switches industriales y otros dispositivos ejecutando el software IOS XE.  
  
  
  

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/vulnerabilidades/los-puntos-de-acceso-wifi-de-cisco-se-pueden-hackear-facilmente-desconectelos-y-proteja-su-red/)

No olvides Compartir... 

  

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)