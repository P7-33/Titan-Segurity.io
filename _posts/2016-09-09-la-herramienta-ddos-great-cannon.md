---
title: 'La herramienta DDoS Great Cannon utilizada contra el foro de
manifestantes de Hong Kong'
date: 2019-12-05T03:56:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Hj15LsTAiTg/XehxypPXbWI/AAAAAAAALbo/LQ6Cfb1AAyg2k3bUOjX3dvcQQ_VJ7kveQCLcBGAsYHQ/s640/neo-urban-1734495_960_720.jpg)](https://1.bp.blogspot.com/-Hj15LsTAiTg/XehxypPXbWI/AAAAAAAALbo/LQ6Cfb1AAyg2k3bUOjX3dvcQQ_VJ7kveQCLcBGAsYHQ/s1600/neo-urban-1734495_960_720.jpg)

La herramienta de denegación de servicio distribuida Great Cannon (DDoS) se implementó nuevamente para lanzar ataques contra la plataforma de medios sociales LIHKG utilizada por los manifestantes de Hong Kong para coordinar durante las protestas contra la extradición de este año.  
  
Los atacantes usan el Gran Cañón para consumir los recursos de un sitio web específico fuera del Gran Cortafuegos de China (GFW) con tráfico web superfluo proveniente de usuarios chinos a quienes se les inyectaron sus conexiones HTTP inseguras con código JavaScript malicioso al visitar sitios inseguros.  
  
Citizen Lab describe el Gran Cañón como "no simplemente una extensión del Gran Firewall, sino una herramienta de ataque distinta que secuestra el tráfico a (o presumiblemente) las direcciones IP individuales, y puede reemplazar arbitrariamente el contenido no cifrado como un hombre en el medio ".  
  
El sitio web LIHKG con sede en Hong Kong dirigido con este dispositivo de asedio DDoS se utiliza como plataforma para varios otros propósitos además de organizar las protestas sin líderes y se comparó con Reddit en los informes de los medios.

  
  

![Great Cannon operation](https://www.bleepstatic.com/images/news/u/1109292/December 2019/Great Cannon operation.png)

**Great Cannon operation** (_Image: AT&T Alien Labs_)

Foro LIHKG convertido en carne de cañón  
  
"El Gran Cañón actualmente está intentando desconectar el sitio web LIHKG. LIHKG se ha utilizado para organizar protestas en Hong Kong", descubrió el ingeniero de amenazas de AT&T Alien Labs, Chris Doman.  
  
Los ataques contra el sitio de redes sociales LIHKG se iniciaron el 31 de agosto utilizando un código malicioso muy similar al utilizado en ataques anteriores contra el sitio web de noticias en idioma chino Mingjingnews a partir de 2017.  
  
LIHKG dijo en una declaración oficial que tienen "razones para creer que existe un poder, o incluso un poder a nivel nacional para organizar ataques como botnets de todo el mundo que fueron manipulados para lanzar este ataque".  
  
Estas son las cifras sobre el ataque durante el período 08:00 - 23:59 del 31 de agosto de 2019:  
  
\- La solicitud total superó los 1.500 millones;  
\- El récord más alto en visitantes únicos excedió 6.5 millones / hora;  
\- El registro más alto en la frecuencia de solicitud total fue de 260k / seg en el que luego duró 30 minutos antes de que se prohibiera.  
  
El código JavaScript se sirvió desde http \[:\] // push.zhanzhang.baidu.com/push\[.font>js y http \[:\] // js.passport.qihucdn.com/11.0.1\[.font>js.  
  
Si bien las dos URL se utilizan para entregar secuencias de comandos de seguimiento analítico, Great Cannon intercambiará las secuencias de comandos de seguimiento benignas e inyectará su propio código malicioso diseñado para solicitar una multitud de recursos web de los sitios web en su lista de destino, intentando abrumarlos y desencadenar una Denegación de estado de servicio (DoS).  
  
Aunque al principio, una sola página de LIHKG fue atacada, los actores de la amenaza detrás del asedio DDoS luego cambiaron a atacar "varias páginas e intentaron (sin éxito) evitar las mitigaciones DDoS que los propietarios del sitio web habían implementado".

  
  

![Malicious code used to bypass DDoS mitigations](https://www.bleepstatic.com/images/news/u/1109292/December 2019/Malicious code used to bypass DDoS mitigations.png)

**Malicious code used to bypass DDoS mitigations** (_Image: AT&T Alien Labs_)

"Es poco probable que estos sitios se vean seriamente afectados. En parte debido a que LIHKG está detrás de un servicio anti-DDoS, y en parte debido a algunos errores en el código malicioso Javascript", agregó Doman.  
  
"Aún así, es inquietante ver que una herramienta de ataque con el poder potencial del Gran Cañón se usa con más frecuencia y nuevamente causa daños colaterales a los servicios con base en los Estados Unidos".  
  
También recomienda sitios que podrían ser el objetivo de tal ataque para bloquear las URL de los recursos de seguimiento de análisis si no se sirven a través de una conexión HTTPS segura.

  

**Una breve historia del Gran Cañón**  
  
El Gran Cañón se vio por primera vez en acción durante una fase de prueba inicial detectada por el Equipo de Seguridad de Google con la ayuda de la infraestructura de Navegación segura entre el 3 y el 6 de marzo de 2015.  
  
El 16 de marzo de 2015, el Gran Cañón resurgió durante los ataques contra los servicios Amazon CloudFront alquilados por GreatFire.org, una organización conocida por monitorear y luchar contra la censura china.  
  
"El ataque envió 2.600 millones de solicitudes por hora a GreatFire y llevó los costos de ancho de banda de la organización con Amazon a $ 30,000 por día", dice Young Xu de ThousandEyes.  
  
"En este caso en particular, los recursos Javascript y HTML alojados en baidu.com fueron reemplazados por Javascript que solicitaría repetidamente recursos de los dominios atacados", declaró el ingeniero del equipo de seguridad de Google, Niels Provos, en ese momento, más tarde ese mes, los servidores de GitHub fueron también el objetivo de un ataque DDoS, y la compañía lo llamó el "ataque DDoS (denegación de servicio distribuido) más grande en la historia de github.com".  
  
Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/the-great-cannon-ddos-tool-used-against-hong-kong-protestors-forum/)  

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)