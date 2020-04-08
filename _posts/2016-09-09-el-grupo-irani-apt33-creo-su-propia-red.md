---
title: 'El grupo iraní APT33 creó su propia red VPN, pero esto solo dañó la
privacidad'
date: 2019-11-18T03:31:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-BuIV1iw4QTE/XdKfXfkfSiI/AAAAAAAALV0/uWJdFyMSizoYr1v-QH-G-tRadK_fJGOsgCLcBGAsYHQ/s640/vpn-2714263_960_720.jpg)](https://1.bp.blogspot.com/-BuIV1iw4QTE/XdKfXfkfSiI/AAAAAAAALV0/uWJdFyMSizoYr1v-QH-G-tRadK_fJGOsgCLcBGAsYHQ/s1600/vpn-2714263_960_720.jpg)

  
Los analistas de Trend Micro han estado observando durante mucho tiempo al grupo de piratas iraníes APT33, que ha estado activo desde al menos 2013 y, en particular, está detrás de la creación del famoso Shamoon [malvari](https://xakep.ru/2018/12/14/shamoon-v3/) . En 2019, las víctimas de APT33 era una empresa estadounidense privada que brindaba servicios de seguridad nacional, universidades y colegios en los Estados Unidos, así como una serie de empresas y organizaciones en el Medio Oriente y Asia.

Durante mucho tiempo estudiando la actividad de APT33, los investigadores [pudieron descubrir](https://blog.trendmicro.com/trendlabs-security-intelligence/more-than-a-dozen-obfuscated-apt33-botnets-used-for-extreme-narrow-targeting/) cómo el grupo administra su infraestructura, que es un sistema de múltiples capas y aislado diseñado para ocultar la actividad de los operadores de APT33 a la atención de especialistas. Los analistas escriben que hay cuatro niveles de protección entre los operadores APT33 y sus objetivos:

*   Nivel VPN: una red especialmente construida de nodos VPN necesarios para ocultar la dirección IP real y la ubicación del operador;
*   Nivel de controlador Bot: un nivel intermedio de servidores;
*   nivel de back-end del servidor de administración: los servidores internos reales a través de los cuales el grupo administra sus botnets;
*   nivel de proxy: un conjunto de servidores proxy en la nube a través del cual los servidores de administración se esconden con hosts infectados.

[![](https://xakep.ru/wp-content/uploads/2019/11/248378/APT33-Infection-Chain-1-01.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/11/248378/APT33-Infection-Chain-1-01.jpg#26759185)

Pero, como resultó, APT33 nunca usa servidores VPN comerciales para ocultar su ubicación, como lo hacen otros grupos. En cambio, los hackers crearon su propia red VPN, porque no es difícil alquilar un par de servidores y usar software de código abierto (por ejemplo, OpenVPN). Sin embargo, esto es precisamente lo que finalmente facilitó el seguimiento de las agrupaciones por parte de los investigadores.

El hecho es que, como resultado, los especialistas de Trend Micro encontraron suficiente para observar solo unas pocas direcciones IP. Y si APT33 usara VPN comerciales, su actividad se perdería fácilmente entre otro tráfico. "APT33 probablemente solo usa sus nodos VPN de salida", escriben los expertos de Trend Micro. "Hemos estado rastreando algunos de los nodos de salida privados del grupo VPN durante más de un año, y hemos enumerado las direcciones IP que conocemos en la tabla a continuación".

[![](https://xakep.ru/wp-content/uploads/2019/11/248378/apt33-vpns.png#26759185)](https://xakep.ru/wp-content/uploads/2019/11/248378/apt33-vpns.png#26759185)

Curiosamente, las VPN propietarias son utilizadas por el grupo no solo para conectarse a los paneles de control de botnet, sino también para otras tareas, incluido el reconocimiento de redes relacionadas con la industria petrolera. Entonces, los investigadores han visto cómo algunas de las direcciones IP anteriores se utilizaron para el reconocimiento en las redes de una compañía petrolera no identificada, hospitales militares en el Medio Oriente, así como una compañía petrolera no identificada en los Estados Unidos.

Dado el interés de APT33 en la industria petrolera (Trend Micro advierte que los piratas informáticos también han visitado sitios utilizados para contratar personas en el sector de petróleo y gas), se aconseja a las empresas que verifiquen los registros de seguridad y busquen las direcciones IP que figuran en ellos  , es decir, asegúrese de que APT33 no esté interesado en ellos.   

Además, los piratas informáticos utilizan una VPN privada para acceder a sitios de varias compañías de pruebas de penetración, correo, sitios de vulnerabilidad y sitios dedicados a piratear criptomonedas.

[![](https://xakep.ru/wp-content/uploads/2019/11/248378/APT33-Infection-Chain-2-01.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/11/248378/APT33-Infection-Chain-2-01.jpg#26759185)  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2019/11/15/apt33-vpn/)

No olvides Compartir...

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)