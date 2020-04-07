---
title: 'Bug Sudo permite a los usuarios de Linux y macOS no privilegiados
ejecutar comandos como root'
date: 2020-02-04T14:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Yv-kuWTifJI/XjlyATvV-lI/AAAAAAAALvQ/An_v8VCEam4TneiEHg7T_zS7Os-gRZsmwCLcBGAsYHQ/s640/sudo-linux-vulnerability%2B%25281%2529.jpg)](https://1.bp.blogspot.com/-Yv-kuWTifJI/XjlyATvV-lI/AAAAAAAALvQ/An_v8VCEam4TneiEHg7T_zS7Os-gRZsmwCLcBGAsYHQ/s1600/sudo-linux-vulnerability%2B%25281%2529.jpg)

  

Joe Vennix, de la seguridad de Apple, ha encontrado otra vulnerabilidad importante en la utilidad sudo que, bajo una configuración específica, podría permitir que usuarios con pocos privilegios o programas maliciosos ejecuten comandos arbitrarios con privilegios administrativos ('root') en sistemas Linux o macOS.

  

Sudo es una de las utilidades más importantes, potentes y de uso común que viene como un comando central preinstalado en macOS y casi todos los sistemas operativos basados ​​en UNIX o Linux.

  

Sudo ha sido diseñado para permitir a los usuarios ejecutar aplicaciones o comandos con los privilegios de un usuario diferente sin cambiar de entorno.

  

**Vulnerabilidad de sudo (CVE-2019-18634)**

  

La vulnerabilidad de escalada de privilegios recientemente descubierta, rastreada como CVE-2019-18634, en cuestión proviene de un problema de desbordamiento de búfer basado en pila que reside en las versiones de Sudo anteriores a 1.8.26.

  

Según Vennix, la falla solo puede explotarse cuando la opción "pwfeedback" está habilitada en el archivo de configuración de sudoers, una característica que proporciona retroalimentación visual, un asterisco (\*), cuando un usuario ingresa la contraseña en el terminal.

  

Cabe señalar que la función pwfeedback no está habilitada de forma predeterminada en la versión anterior de sudo o en muchos otros paquetes. Sin embargo, algunas distribuciones de Linux, como Linux Mint y Elementary OS, lo habilitan en sus archivos de sudoers predeterminados.

  

[![](https://1.bp.blogspot.com/-wxqeawZBgbw/Xjlx5QLXp6I/AAAAAAAALvM/SXxgMP_58W0LARJg-s0OcR_X2o7nUGwTgCLcBGAsYHQ/s640/sudo-linux-vulnerability.jpg)](https://1.bp.blogspot.com/-wxqeawZBgbw/Xjlx5QLXp6I/AAAAAAAALvM/SXxgMP_58W0LARJg-s0OcR_X2o7nUGwTgCLcBGAsYHQ/s1600/sudo-linux-vulnerability.jpg)

  

Además de esto, cuando pwfeedback está habilitado, la vulnerabilidad puede ser explotada por cualquier usuario, incluso sin los permisos de sudo.

  

"El error puede reproducirse pasando una entrada grande a sudo cuando solicita una contraseña", explicó el desarrollador de Sudo Todd C. Miller. "Debido a que el atacante tiene un control completo de los datos utilizados para desbordar el búfer, existe una alta probabilidad de explotabilidad".

  

**Compruebe si está afectado y aplique parches**

  

Para determinar si la configuración de sudoers se ve afectada, puede ejecutar el comando "sudo -l" en su terminal Linux o macOS para averiguar si la opción "pwfeedback" está habilitada y listada en la salida "Entradas de valores predeterminados coincidentes".

  

Si está habilitado, puede deshabilitar el componente vulnerable cambiando "Defaults pwfeedback" a "Defaults! Pwfeedback" en el archivo de configuración de sudoers para evitar la explotación de la vulnerabilidad de escalada de privilegios.

  

Vennix informó de manera responsable la vulnerabilidad a los mantenedores de Sudo, quienes a fines de la semana pasada lanzaron sudo versión 1.8.31 con un parche.

  

"Si bien el error lógico también está presente en las versiones de sudo 1.8.26 a 1.8.30, no es explotable debido a un cambio en el manejo de EOF introducido en sudo 1.8.26", dijo Miller.

  

Apple también lanzó una actualización de parche para macOS High Sierra 10.13.6, macOS Mojave 10.14.6, macOS Catalina 10.15.2 la semana pasada.

  

Joe Vennix informó el año pasado una vulnerabilidad de impacto similar en Sudo que podría haber sido explotada por un atacante para ejecutar comandos como root simplemente especificando el ID de usuario "-1" o "4294967295".  
  
  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2020/02/sudo-linux-vulnerability.html)

No olvides Compartir... 

  

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)