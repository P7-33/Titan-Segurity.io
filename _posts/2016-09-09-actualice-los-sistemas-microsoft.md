---
title: 'Actualice los sistemas Microsoft Windows para parchear 99 nuevas fallas
de seguridad'
date: 2020-02-14T05:09:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-7vxZgNy30us/Xkaa9_BfvkI/AAAAAAAALy0/hg4M4fJDABIOrAOSwSKZ9GiqWZUtL-WegCLcBGAsYHQ/s640/microsoft-windows-patch-update.jpg)](https://1.bp.blogspot.com/-7vxZgNy30us/Xkaa9_BfvkI/AAAAAAAALy0/hg4M4fJDABIOrAOSwSKZ9GiqWZUtL-WegCLcBGAsYHQ/s1600/microsoft-windows-patch-update.jpg)

  

Microsoft emitió su edición Patch Tuesday de febrero de 2020 con parches para un total de 99 nuevas vulnerabilidades.

  

Según las advertencias, 12 de los problemas totales parcheados por el gigante tecnológico este mes son de gravedad crítica, y los 87 restantes se han enumerado como importantes.

  

Cinco de los errores se enumeran como conocidos públicamente en el momento del lanzamiento, cuatro de los cuales son importantes en severidad y uno crítico (CVE-2020-0674) que también se encuentra bajo ataque activo.

  

Microsoft advirtió sobre esta vulnerabilidad de día cero en el navegador Internet Explorer (IE) el mes pasado cuando lanzó un aviso sin lanzar un parche para millones de sus usuarios afectados.

  

Como se explicó anteriormente, esta falla podría permitir que un atacante remoto ejecute código arbitrario en computadoras específicas y tome el control total sobre ellas simplemente al convencer a las víctimas de que abran una página web maliciosamente creada en el vulnerable navegador de Microsoft.

  

Todas las versiones compatibles de Microsoft Windows también contienen una falla crítica de RCE (CVE-2020-0662) que un atacante con una cuenta de usuario de dominio puede explotar para ejecutar código arbitrario en el sistema de destino con permisos elevados.

  

Remote Desktop Client también contiene dos problemas críticos, rastreados como CVE-2020-0681 y CVE-2020-0734, que no son errores corregibles, pero podrían usarse para comprometer sistemas vulnerables cuando se conectan a un servidor malicioso o no confiable.

  

"Para explotar esta vulnerabilidad, un atacante necesitaría tener el control de un servidor y luego convencer a un usuario para que se conecte a él. Un atacante no tendría forma de obligar a un usuario a conectarse al servidor malicioso, necesitaría engañar al usuario para conectarse a través de ingeniería social, envenenamiento de DNS o usar una técnica de Hombre en el Medio (MITM) ", dice el aviso.

  

"Un atacante también podría comprometer un servidor legítimo, alojar código malicioso en él y esperar a que el usuario se conecte".

  

Existe otra vulnerabilidad crítica (CVE-2020-0729) que existe en la forma en que el sistema operativo Microsoft Windows analiza los accesos directos LNK, cuya explotación exitosa podría permitir que un atacante remoto ejecute código arbitrario en el sistema afectado y tome el control total de él.

  

"El atacante podría presentar al usuario una unidad extraíble, o recurso compartido remoto, que contenga un archivo .LNK malicioso y un binario malicioso asociado. Cuando el usuario abre esta unidad (o recurso compartido remoto) en el Explorador de Windows o cualquier otra aplicación que analice el archivo .LNK, el binario malicioso ejecutará el código de la elección del atacante en el sistema de destino ", dice el aviso.

  

Además de esto, la mayoría de los otros problemas críticos son fallas de corrupción de memoria en IE, el navegador Edge y el motor de secuencias de comandos Chakra, que, si se explota con éxito, también podría permitir que un atacante remoto no autenticado ejecute código arbitrario en un sistema objetivo en el contexto de El usuario actual.

  

Cabe señalar que hay un importante problema de omisión de características de seguridad (CVE-2020-0689) que representa una amenaza significativa para los usuarios conscientes de la seguridad. Según Microsoft, hay una vulnerabilidad en la función de arranque seguro que podría permitir que un atacante lo omita y cargue software no confiable en el sistema.

  

Las últimas actualizaciones también contienen parches para vulnerabilidades de escalada de privilegios múltiples que afectan a las versiones del sistema operativo Windows, lo que podría permitir a los atacantes con pocos privilegios ejecutar código arbitrario en modo kernel.

  

Se recomienda encarecidamente a los usuarios y administradores de sistemas que apliquen los últimos parches de seguridad lo antes posible para evitar que los ciberdelincuentes y los piratas informáticos tomen el control de sus computadoras.

  

Para instalar las últimas actualizaciones de seguridad, puede dirigirse a Configuración → Actualización y seguridad → Actualización de Windows → Buscar actualizaciones en su computadora, o puede instalar las actualizaciones manualmente.

  
  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2020/02/microsoft-windows-updates.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)