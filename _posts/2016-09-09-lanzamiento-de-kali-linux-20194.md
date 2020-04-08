---
title: 'Lanzamiento de Kali Linux 2019.4'
date: 2019-12-02T20:14:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-k_sX_iu-5PU/XeVhFuRNrYI/AAAAAAAALas/RA5VtLmefXsKrVUXcFcpLEJIYo_KL7PlwCLcBGAsYHQ/s640/kali-2019.4-release.png)](https://1.bp.blogspot.com/-k_sX_iu-5PU/XeVhFuRNrYI/AAAAAAAALas/RA5VtLmefXsKrVUXcFcpLEJIYo_KL7PlwCLcBGAsYHQ/s1600/kali-2019.4-release.png)

  

Estamos increíblemente emocionados de anunciar nuestro cuarto y último lanzamiento de 2019, Kali Linux 2019.4, que está disponible de inmediato para [descargar](https://www.kali.org/downloads/).  
  
2019.4 incluye algunas nuevas actualizaciones emocionantes:  
  
    Un nuevo entorno de escritorio predeterminado, Xfce  
    Nuevo tema GTK3 (para Gnome y Xfce)  
    Introducción del modo "Kali Undercover"  
    La documentación de Kali tiene un nuevo hogar y ahora funciona con Git  
    Empaque público: cómo introducir sus herramientas en Kali  
    Kali NetHunter KeX: escritorio completo de Kali en Android  
    BTRFS durante la configuración  
    PowerShell agregado  
    El núcleo se actualiza a la versión 5.3.9  
    ... Además de las correcciones de errores normales y actualizaciones.  
  
**Nuevo entorno de escritorio y tema GTK3**  
  
Hay un montón de actualizaciones para esta versión, pero lo más importante que todos notarán primero son los cambios en el entorno y el tema del escritorio. Así que cubramos eso primero.  
  
Se ha tardado mucho en actualizar el entorno de escritorio. Hemos estado hablando sobre cómo abordar esto, lo que queríamos hacer, experimentar con diferentes enfoques, y así durante meses. Como resumen, tuvimos algunos problemas que queríamos abordar de frente:  
  
    Problemas de rendimiento: Gnome es un entorno de escritorio con todas las funciones con un montón de cosas increíbles que puede hacer. Pero todas estas características vienen con gastos generales, a menudo gastos generales que no son útiles para una distribución como Kali. Queríamos acelerar las cosas y tener un entorno de escritorio que solo haga lo que se necesita y nada más. Gnome ha sido excesivo para la mayoría de los usuarios de Kali, ya que muchos solo quieren un administrador de ventanas que le permita ejecutar múltiples ventanas de terminal a la vez y un navegador web.

  
    Experiencia de usuario fracturada: admitimos una gama de hardware, desde los más altos hasta los más bajos. Debido a esto, tradicionalmente nuestras compilaciones ARM de gama baja han tenido una interfaz de usuario completamente diferente a nuestro estándar. Eso no es óptimo, y queríamos unificar esta experiencia, por lo que no importaba si estaba ejecutando una instalación de metal desnudo en una computadora portátil de alta gama o usando una Raspberry Pi, la interfaz de usuario debería ser la misma.  
    Apariencia moderna: hemos estado usando la misma interfaz de usuario durante bastante tiempo y nuestro antiguo responsable del tema había avanzado debido a la falta de tiempo. Así que queríamos ir con algo fresco, nuevo y moderno.  
  
Para ayudarnos a abordar estos elementos, rastreamos a Daniel Ruiz de Alegría y comenzamos el desarrollo de un nuevo tema que se ejecuta en Xfce. ¿Por qué Xfce? Después de revisar los problemas anteriores, sentimos que Xfce los abordaba mejor sin dejar de ser accesible para la mayoría de los usuarios.  
  
La solución con la que nos hemos comprometido es liviana y puede ejecutarse en todos los niveles de las instalaciones de Kali. Es funcional porque maneja las diversas necesidades del usuario promedio sin cambios. Es accesible cuando utiliza conceptos de interfaz de usuario estándar con los que todos estamos familiarizados para garantizar que no haya una curva de aprendizaje. Y se ve muy bien con elementos modernos de interfaz de usuario que hacen un uso eficiente del espacio de la pantalla.  
  
Estamos realmente entusiasmados con esta actualización de la interfaz de usuario y creemos que les va a encantar. Sin embargo, como UI puede ser un poco como la religión, si no quieres irte de Gnome no te preocupes. Todavía tenemos una compilación de Gnome para ti, con algunos cambios ya implementados. A medida que pase el tiempo, haremos cambios en todos los entornos de escritorio que lanzamos instalaciones para que estén "cerca" de una experiencia de usuario similar, sin importar qué DE ejecute. Habrá límites para esto, ya que no tenemos los recursos para invertir fuertemente en ajustar todos estos entornos diferentes. Entonces, si hay algo que le gustaría ver, ¡no dude en enviar una solicitud de función!  
  
También hemos publicado un FAQ sobre el nuevo tema que puedes encontrar en nuestra página de documentos. Esto incluye algunos elementos comunes como cómo cambiar al tema en su instalación existente, cómo desactivarlo si no le gusta, y así sucesivamente.

**  
Kali Undercover**  
  
Con el cambio al medio ambiente, pensamos que daríamos un paso al costado y haríamos algo divertido. Gracias a Robert, que lidera nuestro equipo de pruebas de penetración, por sugerir un tema Kali que se parece a Windows a la vista casual, hemos creado el tema Kali Undercover.

  

[![](https://1.bp.blogspot.com/-5IBQisqiFp4/XeVhoNjBhzI/AAAAAAAALa0/ZA3Hbwg51TwC-I7mB7kzhP9NijuLFAMLgCLcBGAsYHQ/s640/kali-undercover-1.gif)](https://1.bp.blogspot.com/-5IBQisqiFp4/XeVhoNjBhzI/AAAAAAAALa0/ZA3Hbwg51TwC-I7mB7kzhP9NijuLFAMLgCLcBGAsYHQ/s1600/kali-undercover-1.gif)

Digamos que está trabajando en un lugar público, pirateando, y es posible que no desee el distintivo dragón de Kali para que todos lo vean y se pregunten qué está haciendo. Entonces, creamos un pequeño script que cambiará su tema Kali para que parezca una instalación predeterminada de Windows. De esa manera, puedes trabajar un poco más de incógnito. Una vez que haya terminado y en un lugar más privado, ejecute el script nuevamente y cambie de nuevo a su tema Kali. ¡Como magia!  
  
Para más información visitar [https://www.kali.org/news/kali-linux-2019-4-release/](https://www.kali.org/news/kali-linux-2019-4-release/) 

  

Fuente: [https://www.kali.org/](https://www.kali.org/news/kali-linux-2019-4-release/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)