---
title: 'Los proveedores de servicios, en el punto de mira de los ataques DDoS'
date: 2020-02-17T03:05:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-KFA2IOZyjEU/Xkn0t6Tq81I/AAAAAAAALzc/HxoFkuKaceEg1j3UR98wcRzPnVABhDnlQCLcBGAsYHQ/s640/Ayer-hubo-un-ataque-DDoS-masivo-contra-las-principales-webs.jpg)](https://1.bp.blogspot.com/-KFA2IOZyjEU/Xkn0t6Tq81I/AAAAAAAALzc/HxoFkuKaceEg1j3UR98wcRzPnVABhDnlQCLcBGAsYHQ/s1600/Ayer-hubo-un-ataque-DDoS-masivo-contra-las-principales-webs.jpg)

  

Lejos de disminuir, los ataques distribuidos de denegación de servicio (DDoS) dirigidos a los proveedores de servicios están aumentando de forma exponencial. Esto es al menos lo que pone de relieve un informe elaborado por F5 Labs1 y para el cual ha tomado en cuenta los **incidentes de seguridad en redes fijas y móviles durante los últimos tres años**.

  

El informe señala de la misma forma que otro tipo de ataques, como los de fuerza bruta, a pesar de seguir siendo importantes, son **cada vez menos numerosos**. Asimismo, afirma que los ataques de inyección web y el ataque a  dispositivos son también amenazas relevantes.

  

“En general, los proveedores de servicios han hecho avances importantes en la defensa de sus redes, pero todavía hay mucho margen de mejora. Esto es particularmente cierto cuando se trata de detectar ataques de forma temprana sin comprometer la capacidad de escalar y de satisfacer la demanda de los clientes“, ha explicado Malcolm Heath, Senior Threat Research Evangelist en F5 Labs.

### Los DDoS, en ascenso

Pero como proclama el informe, los ataques DDoS fueron, con mucho, la mayor amenaza para los proveedores de servicios entre 2017 y 2019, representando el **49% de todos los incidentes reportados durante este período. **Y lo que es peor, mientras que en 2017 representaron el 25% de los ataques registrados, el año pasado crecieron hasta el 77%.

  

Como target principal, este tipo de ataques se focalizaron en los sistemas de nombre de dominio (DNS) o en aplicaciones financieras.

  

F5 Labs señala que la mayoría de los incidentes DDoS reportados se centraron en DNS, como los ataques de reflexión y los DNS Water Torture. Los ataques de reflexión utilizan recursos alojados por el proveedor de servicios (como DNS y NTP) para reflejar tráfico falso con la finalidad de que las respuestas del servicio utilizado vayan al objetivo, no al iniciador.

  

DNS Water Torture es una forma de ataque de reflexión que utiliza peticiones incorrectas de forma intencionada para generar una mayor carga en los servidores DNS objetivo. Sin embargo, las solicitudes pasan a través de los servidores DNS locales del proveedor de servicios, lo que genera mayores tensiones que, en ocasiones, llegan al nivel de denegación de servicio.

  

La primera prueba de un ataque suele ser un aumento en el tráfico de red descubierto por el equipo de operaciones de un proveedor de servicios. Otras señales de alerta incluyen quejas de clientes provocadas por un servicio de red lento o por servidores DNS que no responden.

### Ataques de autenticación, significativos pero en retroceso

Los ataques de fuerza bruta, que implican probar cantidades masivas de nombres de usuario y contraseñas contra un punto de autenticación, fueron el segundo incidente más reportado. Los atacantes a menudo usan credenciales obtenidas en otras brechas, que luego se utilizan para atacar servicios a través de una táctica conocida como «relleno de credenciales».

  

Otras formas de ataques de fuerza bruta simplemente usan listas comunes de credenciales predeterminadas (es decir, admin/admin), contraseñas utilizadas comúnmente o cadenas de contraseñas generadas al azar.

  

En este punto se observa una marcada recesión en los ataques de fuerza bruta, ya que si en 2017 fueron el 72% de todos los incidentes, **en 2019 bajaron hasta el 20%**. Sin embargo, hubo un aumento en los ataques de este tipo a proveedores de servicios centrados en el sector financiero.

### Dispositivos comprometidos, ataques web y bots de IoT

Otros ataques destacables registrados por la compañía son los relacionados con dispositivos comprometidos dentro de la infraestructura de proveedor de servicios, que representaron el 8% de los incidentes en 2018. Por lo general, se detectaron debido al aumento del tráfico saliente, ya que los dispositivos comprometidos se usaban para lanzar ataques de denegación de servicio.

  

F5 Labs dice que los ataques a la red general representaron también el 8% de todos los incidentes en 2019, con las inyecciones dominando como táctica específica. Los ataques intentan aprovechar los **errores en el código de la aplicación web** para solicitar la ejecución del comando.

  

En el caso de una inyección SQL, se intenta ejecutar comandos en servidores de bases de datos back-end, lo que a menudo conduce a la exfiltración de datos. Tales ataques generalmente son capturados por tecnologías WAF o por alertas activadas desde los registros del servidor web.

  

En el frente de Internet de las cosas (IoT), **la influencia de un bot llamado Annie**, una variante de Mirai, continuó ejerciendo influencia. Descubierto por primera vez en 2016, el bot apunta a los protocolos personalizados TR-069 y TR-064 utilizados por los ISPs para administrar de forma remota grandes flotas de routers a través del puerto 7547.

  

Aunque el actor de la amenaza que creó Annie admitió no usar el bot desde diciembre de 2016, dirigirse al puerto 7547 sigue siendo frecuente y continuó intensificándose en 2019. El interés de los atacantes por el puerto de administración remota Mikrotik 8291 también ha aumentado exponencialmente en los últimos seis meses.

  

Fuente: [https://www.muyseguridad.net/](https://www.muyseguridad.net/2020/02/13/ataques-ddos-provvedores-servicios/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)