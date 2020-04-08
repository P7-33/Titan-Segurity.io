---
title: 'La falla de Sudo permite a los usuarios de Linux ejecutar comandos como
raíz incluso cuando están restringidos'
date: 2019-10-15T03:45:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-8I70XLYejCQ/XaY_RknWwhI/AAAAAAAALIo/fYdZNxvd_asNFH22Gq65chX_m62VKy8TQCLcBGAsYHQ/s640/linux-sudo-hacking.png)](https://1.bp.blogspot.com/-8I70XLYejCQ/XaY_RknWwhI/AAAAAAAALIo/fYdZNxvd_asNFH22Gq65chX_m62VKy8TQCLcBGAsYHQ/s1600/linux-sudo-hacking.png)

  
¡Atención usuarios de Linux!

  

Se ha descubierto una nueva vulnerabilidad en Sudo, una de las utilidades más importantes, potentes y de uso común que viene como un comando central instalado en casi todos los sistemas operativos basados ​​en UNIX y Linux.

  

La vulnerabilidad en cuestión es un problema de omisión de la política de seguridad de sudo que podría permitir que un usuario malintencionado o un programa ejecute comandos arbitrarios como root en un sistema Linux objetivo, incluso cuando la "configuración de sudoers" no permite explícitamente el acceso de root.

  

  

Sudo, que significa "superusuario do", es un comando del sistema que permite a un usuario ejecutar aplicaciones o comandos con los privilegios de un usuario diferente sin cambiar de entorno, la mayoría de las veces, para ejecutar comandos como usuario root.

  

De manera predeterminada en la mayoría de las distribuciones de Linux, la palabra clave ALL en la especificación RunAs en el archivo / etc / sudoers, como se muestra en la captura de pantalla, permite a todos los usuarios en los grupos admin o sudo ejecutar cualquier comando como cualquier usuario válido en el sistema.

  

[![](https://1.bp.blogspot.com/-LpgTkTws8fE/XaY_oATdpkI/AAAAAAAALIw/yYDTs3_ulNEer5Wkae4QmLqOiVlu7iyWQCLcBGAsYHQ/s640/11.png)](https://1.bp.blogspot.com/-LpgTkTws8fE/XaY_oATdpkI/AAAAAAAALIw/yYDTs3_ulNEer5Wkae4QmLqOiVlu7iyWQCLcBGAsYHQ/s1600/11.png)

  

  

Sin embargo, dado que la separación de privilegios es uno de los paradigmas de seguridad fundamentales en Linux, los administradores pueden configurar un archivo sudoers para definir qué usuarios pueden ejecutar qué comandos y qué usuarios.

  

Por lo tanto, en un escenario específico donde se le ha permitido ejecutar un comando específico, o cualquier otro, como cualquier otro usuario, excepto la raíz, la vulnerabilidad aún podría permitirle eludir esta política de seguridad y tomar el control completo sobre el sistema como raíz.

  

"Esto puede ser utilizado por un usuario con suficientes privilegios de sudo para ejecutar comandos como root, incluso si la especificación Runas no permite explícitamente el acceso root siempre y cuando la palabra clave ALL aparezca primero en la especificación Runas", dicen los desarrolladores de Sudo.

  

¿Cómo explotar este error? Solo Sudo ID de usuario -1 o 4294967295

  

La vulnerabilidad, rastreada como CVE-2019-14287 y descubierta por Joe Vennix de Apple Information Security, es más preocupante porque la utilidad sudo ha sido diseñada para permitir a los usuarios usar su propia contraseña de inicio de sesión para ejecutar comandos como un usuario diferente sin requerir su contraseña.

  

Cortafuegos de aplicaciones web

  

Lo que es más interesante es que esta falla puede ser explotada por un atacante para ejecutar comandos como root simplemente especificando el ID de usuario "-1" o "4294967295".

  

Esto se debe a que la función que convierte la identificación de usuario en su nombre de usuario trata incorrectamente -1, o su equivalente no firmado 4294967295, como 0, que siempre es la identificación de usuario del usuario raíz.

  

[![](https://1.bp.blogspot.com/-eIw6nNrUXVs/XaY_xF8rSEI/AAAAAAAALI0/9psxvZHyAy8aLP-dKLE1Ecihgde-N7QFACLcBGAsYHQ/s640/root-hacking.png)](https://1.bp.blogspot.com/-eIw6nNrUXVs/XaY_xF8rSEI/AAAAAAAALI0/9psxvZHyAy8aLP-dKLE1Ecihgde-N7QFACLcBGAsYHQ/s1600/root-hacking.png)

  

  

"Además, debido a que el ID de usuario especificado a través de la opción -u no existe en la base de datos de contraseñas, no se ejecutarán módulos de sesión PAM".

  

La vulnerabilidad afecta a todas las versiones de Sudo anteriores a la última versión lanzada 1.8.28, que se lanzó hoy, hace unas horas y pronto se implementará como una actualización por varias distribuciones de Linux para sus usuarios.

  

Dado que el ataque funciona en un caso de uso específico del archivo de configuración de sudoers, no debería afectar a un gran número de usuarios. Sin embargo, si usa Linux, aún se recomienda encarecidamente actualizar el paquete sudo a la última versión tan pronto como esté disponible.  
  
  
Fuente: [https://thehackernews.com/](https://thehackernews.com/2019/10/linux-sudo-run-as-root-flaw.html)  

No olvides Compartir... 

  
  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)