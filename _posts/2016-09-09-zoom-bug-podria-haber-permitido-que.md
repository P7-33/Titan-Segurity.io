---
title: 'Zoom Bug podría haber permitido que personas no invitadas se unan a
reuniones privadas'
date: 2020-01-28T21:54:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-rRf3eOvMbs8/XjCY7wtzUbI/AAAAAAAALs4/L7v9eG0MIDEtRDGDj35YUybP-_y_VQ5lACLcBGAsYHQ/s640/zoom-software-security.jpg)](https://1.bp.blogspot.com/-rRf3eOvMbs8/XjCY7wtzUbI/AAAAAAAALs4/L7v9eG0MIDEtRDGDj35YUybP-_y_VQ5lACLcBGAsYHQ/s1600/zoom-software-security.jpg)

  

Si usa Zoom para organizar sus reuniones remotas en línea, debe leer este artículo detenidamente.

  

El software de videoconferencia masivamente popular ha solucionado un vacío de seguridad que podría haber permitido a cualquier persona espiar remotamente reuniones activas sin protección, exponiendo potencialmente audio, video y documentos privados compartidos a lo largo de la sesión.

  

Además de organizar reuniones virtuales y seminarios web protegidos con contraseña, Zoom también permite a los usuarios configurar una sesión para participantes no registrados previamente que pueden unirse a una reunión activa ingresando una ID de reunión única, sin requerir una contraseña o pasar por las salas de espera.

  

Zoom genera esta ID de reunión aleatoria, compuesta por números de 9, 10 y 11 dígitos, para cada reunión que programe o cree. Si se filtra más allá de un grupo de personas individual o previsto, el simple hecho de conocer las ID de las reuniones podría permitir que invitados no deseados se unan a reuniones o seminarios web.

  

Esto podría ser una mala noticia para cualquiera que espere que sus conversaciones sean privadas.

  

[![](https://1.bp.blogspot.com/-33Gjugm0Ld8/XjCY0IJqFHI/AAAAAAAALs0/qdDf_12lE7o5L5gODKwKVsYln6y7N5orgCLcBGAsYHQ/s640/zoom-software-hacking.jpg)](https://1.bp.blogspot.com/-33Gjugm0Ld8/XjCY0IJqFHI/AAAAAAAALs0/qdDf_12lE7o5L5gODKwKVsYln6y7N5orgCLcBGAsYHQ/s1600/zoom-software-hacking.jpg)

  

  

Para eludir tales escenarios, Zoom a fines del año pasado introdujo algunos controles adicionales bajo la configuración de contraseña para reuniones y seminarios web, que según Check Point, fue el resultado de una investigación sobre la laguna de seguridad que la empresa de seguridad informó responsablemente a la compañía en julio de 2019.

  

En un informe compartido con The Hacker News antes de su lanzamiento, los investigadores de Check Point demostraron un ataque de enumeración automatizado pero no sofisticado para identificar identificaciones de reuniones aleatorias válidas en lugar de utilizar la técnica de fuerza bruta.

  

"Un pirata informático podría generar previamente una larga lista de ID de Zoom Meeting, usar técnicas de automatización para verificar rápidamente si una ID de Zoom Meeting respectiva era válida o no, y luego obtener acceso a reuniones de Zoom que no estuvieran protegidas con contraseña", afirmaron los investigadores.

  

"Pudimos predecir ~ 4% de las ID de reunión generadas aleatoriamente, lo que es una posibilidad muy alta de éxito, en comparación con la fuerza bruta pura".

  

Como resultado de la divulgación de Check Point, Zoom introdujo las siguientes características y funcionalidades de seguridad en su servicio de videoconferencia basado en la nube:

  

Contraseñas predeterminadas Zoom

  

Zoom ahora, de manera predeterminada, genera automáticamente una contraseña numérica de seis dígitos para cada reunión que cree que los participantes deben ingresar al unirse ingresando manualmente la ID de la reunión.

  

Aplicación de contraseña de nivel de cuenta y grupo: bajo nuevos controles, el administrador de la cuenta puede hacer cumplir tres nuevas configuraciones de contraseña en los niveles de cuenta, grupo y usuario.

  

Validación de ID de reunión: Zoom ya no indicará automáticamente si una ID de reunión es válida o no válida, lo que dificulta que las secuencias de comandos automáticas determinen reuniones activas. Para cada conexión, la página se cargará e intentará unirse a la reunión. Por lo tanto, un mal actor no podrá reducir rápidamente el grupo de reuniones para intentar unirse.

  

Bloqueador de dispositivos: para evitar ataques de fuerza bruta, los intentos repetidos de escanear en busca de identificaciones de reuniones harán que el dispositivo se bloquee por algún tiempo.

  

"La privacidad y seguridad de los usuarios de Zoom es nuestra principal prioridad. El problema se abordó en agosto de 2019, y hemos seguido agregando características y funcionalidades adicionales para fortalecer aún más nuestra plataforma. Agradecemos al equipo de Check Point por compartir sus investigaciones y colaborar con nosotros ", dijo un portavoz de Zoom a The Hacker News.

  

En julio del año pasado, Zoom fue noticia tras una grave vulnerabilidad de seguridad en su aplicación cliente para macOS que permitió a atacantes remotos o sitios web maliciosos encender la cámara del dispositivo de los usuarios sin su permiso o conocimiento.

  
  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2020/01/zoom-meeting-password.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)