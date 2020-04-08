---
title: 'Linux vs Zombieland v2: la batalla de seguridad continúa'
date: 2019-11-15T02:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-OF-nrZpjCRQ/Xc4AVpy7wDI/AAAAAAAALVM/SuZLVC4XPdU9XCZo2Ol-xCpH9aIskR1RwCLcBGAsYHQ/s400/intel-3064506_960_720.webp)](https://1.bp.blogspot.com/-OF-nrZpjCRQ/Xc4AVpy7wDI/AAAAAAAALVM/SuZLVC4XPdU9XCZo2Ol-xCpH9aIskR1RwCLcBGAsYHQ/s1600/intel-3064506_960_720.webp)

  
Otro día, otro error de CPU de Intel. Esto es lo que Red Hat y otros proveedores de Linux están haciendo al respecto.

  
**Estas son las malas noticias:** seguiremos viendo los agujeros fundamentales de seguridad de la CPU Intel apareciendo hasta que cada una de las generaciones actuales de estos chips esté en los vertederos. Zombieland v2 es solo el último de una línea de problemas, que se remonta a Meltdown y Spectre. La "buena" noticia es por ahora Intel y las compañías de sistemas operativos se están adelantando a los hackers. Esto es lo que Linux y Red Hat están haciendo con respecto a las últimas novedades.  
  
Primero, Zombieland v2 no es solo una preocupación para las personas que usan procesadores Intel más antiguos. No, esta confusión de agujeros de seguridad también se puede usar contra todos los procesadores Intel recientes, incluido el último y mejor Cascade Lake.  
  
Específicamente, Zombieland v2 se compone de tres problemas:  
  
Exposiciones y vulnerabilidades comunes (CVE) -2018-12207: Error de verificación de máquina en cambio de tamaño de página.

  
CVE-2019-11135: Aborto asíncrono TSX

CVE-2019-0155 y CVE-2019-0154: agujeros de controlador de gráficos i915.  
  
Cuando se explotan, estos agujeros de seguridad permiten a los atacantes obtener acceso de lectura a sus datos o colgar su sistema  
  
Estos son ataques de Microarchitectural Data Sampling (MDS). Para proteger sus sistemas, debe parchear tanto la actualización del microcódigo de la CPU Intel como el sistema operativo. Hacer solo uno u otro no es suficiente.  
  
Los desarrolladores de Linux, así como sus homólogos en Apple y Microsoft, están listos con parches. Desde Red Hat, que tiende a liderar el camino con la seguridad de Linux, es el primero que es el más problemático. Le da una clasificación de seguridad de importante.  
  
Específicamente, el error de cambio de tamaño de página puede ser utilizado por un atacante privilegiado dentro de una máquina virtual (VM) invitada para bloquear la CPU. Esto, a su vez, puede derribar todo el sistema. Esto no es lo que quiere una VM en sus servidores, o peor aún, su nube.  
  
El hecho de que los otros dos no sean tan malos no significa que pueda descuidarlos. Ambos se pueden usar para espiar a otros usuarios o para bloquear sistemas.  
  
Desafortunadamente, aunque nadie ha hecho benchmarking todavía, es un hecho que verás éxitos de rendimiento. La primera versión de Zombieland ralentizó los servidores hasta en un 40% en algunas cargas de trabajo.  
  
¿Rendimiento o seguridad? Es tu elección, pero sé cuál elegiría. Para citar a Red Hat: "Red Hat sugiere encarecidamente que los usuarios actualicen todos los sistemas, incluso si no creen que su configuración represente una amenaza directa".  
  
Los parches están disponibles para [Red Hat Enterprise Linux (RHEL)](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) a través del [Portal del cliente de Red Hat](https://access.redhat.com/). Puede encontrar los parches necesarios para Ubuntu en la [Base de conocimiento de Ubuntu Wiki](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/TAA_MCEPSC_i915). Para [SUSE Linux Enterprise Server (SLES)](https://www.suse.com/products/server/), consulte la página de actualización de SUSE.  
  
¿Entonces, Qué esperas? ¿Para que los servidores de su centro de datos se apaguen y sus alarmas se apaguen? Consigue parches. Ahora.  

  

  

Fuente: [https://www.zdnet.com/](https://www.zdnet.com/article/linux-vs-zombieland-v2-the-security-battle-continues/)

No olvides Compartir...

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)