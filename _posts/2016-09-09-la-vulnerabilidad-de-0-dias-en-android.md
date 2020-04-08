---
title: 'La vulnerabilidad de 0 días en Android es peligrosa para los
dispositivos Samsung, Xiaomi, Pixel, etc.'
date: 2019-10-08T22:15:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-a9HTIznSuUk/XZz623NSFoI/AAAAAAAALF8/bGhOPXgLJ3stGSOUpkuvcvjmbzdrv_S1wCLcBGAsYHQ/s320/icon-1971128_960_720.png)](https://1.bp.blogspot.com/-a9HTIznSuUk/XZz623NSFoI/AAAAAAAALF8/bGhOPXgLJ3stGSOUpkuvcvjmbzdrv_S1wCLcBGAsYHQ/s1600/icon-1971128_960_720.png)

Los analistas del equipo de Google Project Zero [encontraron un](https://bugs.chromium.org/p/project-zero/issues/detail?id=1942) error peligroso en el kernel de Android al que muchos dispositivos Android son vulnerables. Según los investigadores, esta vulnerabilidad de día cero ya está bajo ataque. El problema puede ayudar a un atacante a obtener acceso de root al dispositivo de destino.

Esta vulnerabilidad se corrigió originalmente en el kernel 4.14 LTS Linux en diciembre de 2017. Esta solución se incluyó en los núcleos Android 3.18, 4.14, 4.4 y 4.9, sin embargo, las versiones más nuevas seguían siendo vulnerables por alguna razón. Como resultado, el error puede representar una amenaza para los siguientes modelos de dispositivos Android con Android 8.xy versiones posteriores:

*   Pixel 2 con Android 9 y Android 10 preview;
*   Huawei P20;
*   Xiaomi Redmi 5A;
*   Xiaomi Redmi Note 5;
*   Xiaomi A1;
*   Oppo A3;
*   Moto Z3;
*   Teléfonos inteligentes Oreo LG
*   Samsung S7, S8, S9.

Peor aún, los expertos escriben que el exploit de la vulnerabilidad, que ahora lleva el identificador CVE-2019-2215, es lo suficientemente universal como para adaptarse a cualquiera de estos modelos con modificaciones mínimas.

  
  

[![](https://xakep.ru/wp-content/uploads/2019/10/241791/PoC-exploit-demo.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/10/241791/PoC-exploit-demo.jpg#26759185)

PoC explotar

  

Los expertos de Google [creen](https://bugs.chromium.org/p/project-zero/issues/detail?id=1942) que el exploit que encontraron para CVE-2019-2215 es el trabajo de la notoria compañía israelí NSO Group. Permítame recordarle que el Grupo NSO se fundó en 2010 y desde entonces ha estado desarrollando varios malware legales que, junto con exploits durante varios días, vende a gobiernos y servicios especiales en todo el mundo. La compañía se hizo ampliamente conocida en 2016-2017, cuando los especialistas en seguridad de la información descubrieron las poderosas herramientas de espionaje  [Pegasus](https://xakep.ru/2016/08/26/pegasus-3-zerodays-in-ios/)  y  [Chrysaor](https://xakep.ru/2017/04/06/chrysaor/) , desarrolladas por el Grupo NSO y diseñadas para iOS y Android.

Los representantes de ZDNet ya respondieron a estas acusaciones y [le dijeron a los medios](https://www.zdnet.com/article/google-finds-android-zero-day-impacting-pixel-samsung-huawei-xiaomi-devices/) que no tienen nada que ver con el exploit:

> “El Grupo NSO no ha vendido y nunca venderá exploits o vulnerabilidades. Este exploit no tiene nada que ver con NSO, y nuestro trabajo se centra en la creación de productos diseñados para inteligencia con licencia y agencias de aplicación de la ley que salvan vidas ".

Afortunadamente, hay buenas noticias. Fresh 0-day no recibió un estado crítico, ya que esta no es una vulnerabilidad RCE que podría explotarse sin ninguna interacción del usuario. Para explotar este problema, se deberán cumplir varias condiciones. Por lo tanto, un atacante deberá instalar una aplicación maliciosa en el dispositivo objetivo para explotar el error. Cualquier otro vector de ataque, por ejemplo, a través de un navegador, requerirá la creación de una cadena de exploits utilizando otras vulnerabilidades adicionales.

  

El parche para el problema de día cero ya está disponible en Android Common Kernel. Los teléfonos inteligentes Pixel 3 y 3a están en todas las áreas de riesgo, mientras que los dispositivos Pixel 1 y 2 deberían recibir actualizaciones para esta vulnerabilidad como parte de la actualización de octubre.

  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2019/10/07/cve-2019-2215/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)