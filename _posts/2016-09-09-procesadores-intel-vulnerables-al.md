---
title: 'Procesadores Intel vulnerables al problema CacheOut'
date: 2020-01-29T14:15:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-mjAQOzV-1nY/XjGDo1tzebI/AAAAAAAALtI/Fqt_YrTlRk8Yns2_6yOE7nr6KKKRH4h4gCLcBGAsYHQ/s640/CacheOut-384x220.jpg)](https://1.bp.blogspot.com/-mjAQOzV-1nY/XjGDo1tzebI/AAAAAAAALtI/Fqt_YrTlRk8Yns2_6yOE7nr6KKKRH4h4gCLcBGAsYHQ/s1600/CacheOut-384x220.jpg)

  

Los profesionales de seguridad hablaron sobre el nuevo ataque especulativo CacheOut, que podría conducir a la fuga de datos de procesadores Intel, máquinas virtuales y enclaves SGX. El error no afecta a los procesadores AMD, pero los investigadores aún no han probado la estabilidad de los productos ARM e IBM contra los ataques CacheOut.

Permítanme recordarles que los problemas de los procesadores Intel, desafortunadamente, no se agotaron con el descubrimiento de las vulnerabilidades Meltdown y Spectre en 2018. En 2019, los expertos identificaron una serie de nuevos problemas de "procesador" relacionados con el mecanismo especulativo proactivo (o especulativo) para ejecutar comandos, incluidos  [Spoiler](https://xakep.ru/2019/03/07/spoiler/) ,  [RIDL, Fallout y ZombieLoad](https://xakep.ru/2019/05/20/ridl-fallout-zombieload/) ,  [ZombieLoad 2](https://xakep.ru/2019/11/13/zombieload-2/) ,  [NetCAT](https://xakep.ru/2019/09/11/netcat/) ,  [TPM-FAIL](https://xakep.ru/2019/11/13/tpm-fail/) ,  [Plundervolt](https://xakep.ru/2019/12/11/plundervolt/) .

Ahora, los expertos han identificado un nuevo problema en la clase de vulnerabilidad Microarchitectural Data Sampling (MDS), que anteriormente incluía   [RIDL, Fallout y ZombieLoad](https://cpu.fail/) . El nuevo ataque se llamó [CacheOut](https://cacheoutattack.com/)  o  [L1D Eviction  ](https://cacheoutattack.com/)[Sampling (L1DES)](https://mdsattacks.com/#ridl-nng) . El problema fue descrito por expertos de VUSec de la Universidad Libre de Amsterdam, así como por expertos de las Universidades Católica de Graz Technical y Leuven. Además, la Universidad de Michigan también publicó un trabajo de investigación sobre el tema después de un análisis realizado en colaboración con analistas de la Universidad de Adelaida en Australia.

Según los investigadores, el ataque permite eludir la protección de hardware en muchos procesadores Intel (una lista de modelos vulnerables está disponible [aquí](https://software.intel.com/security-software-guidance/insights/processors-affected-l1d-eviction-sampling) ) y permite a un atacante elegir qué datos quiere robar, en lugar de fusionar cualquier información disponible.

A pesar de las últimas correcciones, incluso algunos de los últimos procesadores de Intel que son resistentes al problema Meltdown son vulnerables a CacheOut. Cabe señalar que los ataques en CacheOut requieren acceso local al sistema de destino, y los ataques a través del navegador no son posibles.  
  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2020/01/29/cacheout/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)