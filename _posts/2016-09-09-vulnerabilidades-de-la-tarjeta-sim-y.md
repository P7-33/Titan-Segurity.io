---
title: 'Vulnerabilidades de la tarjeta SIM y ataques de SMS'
date: 2019-10-01T21:57:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Zx51OWRsDX8/XZO6f9vmbfI/AAAAAAAALEg/NVvmmm8GfW0UhtTnYRVWTdg4W_AZiiJQgCLcBGAsYHQ/s640/call-71170_960_720.jpg)](https://1.bp.blogspot.com/-Zx51OWRsDX8/XZO6f9vmbfI/AAAAAAAALEg/NVvmmm8GfW0UhtTnYRVWTdg4W_AZiiJQgCLcBGAsYHQ/s1600/call-71170_960_720.jpg)

Expertos en seguridad de la información le contaron al mundo dos problemas que representan un peligro para la mayor parte de los dispositivos móviles. Además, estos problemas no dependen de la plataforma y el tipo de dispositivos de usuario, ya que están asociados con las tarjetas SIM y los principios de los operadores móviles.

#### Simjacker

El ataque de Simjacker fue descrito por los expertos de AdaptiveMobile Security. Implica el uso de mensajes SMS para transmitir SIM Toolkit (STK) y las instrucciones del navegador S @ T en la tarjeta SIM. Curiosamente, este problema no es solo un concepto, sino que se ha aplicado regularmente en la realidad en los últimos dos años. "Estamos seguros de que este exploit fue desarrollado por una empresa privada específica que trabaja con los gobiernos para monitorear a las personas", escriben los expertos.

Los expertos de AdaptiveMobile no revelan el nombre de la compañía que lleva a cabo estos ataques y, por lo tanto, no está claro si este problema se usa para monitorear criminales y terroristas o para rastrear a disidentes, activistas y periodistas.

Según los investigadores, la misma compañía no identificada ha ampliado el acceso a la red central de SS7 y Diameter, y los objetivos de los ataques Simjacker a menudo se convierten en víctimas de ataques a través de SS7. Aparentemente, los ataques que usan SS7 son una opción menos preferida y alternativa en caso de que Simjacker no funcione. El hecho es que recientemente, los operadores han dedicado mucho más tiempo y energía a proteger su infraestructura SS7 y Diameter, mientras que los ataques Simjacker son baratos y fáciles de ejecutar.

La esencia del ataque es que usando un teléfono inteligente o un módem GSM simple, un atacante envía un mensaje SMS especial que contiene instrucciones ocultas para el Kit de herramientas SIM al dispositivo de la víctima. Estas instrucciones son compatibles con la aplicación del navegador S @ T que se ejecuta en la tarjeta SIM del dispositivo.

STK y S @ T Browser son tecnologías antiguas compatibles con muchas redes móviles y tarjetas SIM. Utilizándolos en su dispositivo, puede, por ejemplo, iniciar un navegador, reproducir sonido o mostrar ventanas emergentes. Anteriormente, los operadores móviles a menudo usaban esto para enviar a los usuarios ofertas promocionales o información de facturación.

El ataque Simjacker implica que el atacante abusa de este mecanismo y ordena al dispositivo de la víctima que transmita datos de ubicación e IMEI, que la tarjeta SIM enviará en un mensaje SMS a un dispositivo de terceros, y el atacante eventualmente podrá encontrar la ubicación de su objetivo.

Al mismo tiempo, las víctimas del ataque no ven ningún mensaje SMS u otros signos de compromiso. Es decir, los atacantes pueden inundar constantemente a sus víctimas con mensajes SMS y, por lo tanto, rastrear su ubicación durante largas semanas o incluso meses. Dado que el ataque Simjacker está dirigido a la tarjeta SIM, no depende de la plataforma y el tipo de dispositivo del usuario.

  
  

[![](https://xakep.ru/wp-content/uploads/2019/10/240935/sim-card-hacking.jpg#26759185)](https://xakep.ru/wp-content/uploads/2019/10/240935/sim-card-hacking.jpg#26759185)

  

  

> "Notamos que los dispositivos de casi todos los fabricantes nos permiten conocer con éxito la ubicación del usuario: Apple, ZTE, Motorola, Samsung, Google, Huawei e incluso dispositivos IoT con tarjetas SIM", escriben los investigadores.

Los expertos de AdaptiveMobile señalan que los ataques de Simjacker se llevan a cabo diariamente en grandes cantidades. Muy a menudo, los números de teléfono se rastrean varias veces al día durante mucho tiempo.

> "Los patrones y la cantidad de dispositivos de rastreo indican que esta no es una operación de rastreo de masa a gran escala, sino una operación para rastrear a un gran número de personas para diversos propósitos, y los objetivos y prioridades de los operadores están cambiando", dicen los expertos.

Los analistas también señalan que los ataques de Simjacker se pueden evitar fácilmente si los operadores prestan atención exactamente a qué código funciona en sus tarjetas SIM. El hecho es que la especificación del navegador S @ T no se ha actualizado desde 2009, y la funcionalidad original, como recibir información sobre el saldo de la cuenta a través de una tarjeta SIM, ha quedado obsoleta y otras tecnologías la han reemplazado. Sin embargo, el antiguo navegador S @ T todavía se usa y está presente en las tarjetas SIM de los operadores móviles en al menos treinta países del mundo.

En total, más de mil millones de personas viven en estos países, y todos corren el riesgo de vigilancia sigilosa con Simjacker. Según los informes de los medios, los operadores de Sprint y T-Mobile dijeron que sus usuarios no resultaron heridos, y los representantes de AT&T aseguraron que su red estadounidense era inmune a tales ataques.

Otros comandos compatibles con S @ T Browser incluyen la capacidad de hacer llamadas, enviar mensajes, apagar la tarjeta SIM, ejecutar comandos de módem AT, abrir navegadores y mucho más. Es decir, al usar ataques Simjacker, no solo puede monitorear a los usuarios, sino también involucrarse en fraudes financieros (llamadas a números premium), espionaje (hacer una llamada y escuchar conversaciones cerca del dispositivo), sabotaje (deshabilitar la tarjeta SIM de la víctima), organizar campañas de información errónea ( enviar SMS / MMS con contenido falso) y así sucesivamente.

Cabe señalar que los ataques Simjacker no son un fenómeno tan nuevo. Por ejemplo, el abuso de las instrucciones STK a nivel teórico fue [descrito](https://xakep.ru/2011/12/22/58058/) en 2011 por el especialista en seguridad de la información Bogdan Aleku. Luego, el experto advirtió que esto se puede usar para enviar SMS a números pagados o crear dificultades para recibir mensajes de texto regulares. Un ataque similar también se demostró en 2013 [en la conferencia Black Hat](https://media.blackhat.com/us-13/us-13-Nohl-Rooting-SIM-cards-Slides.pdf) .

#### SMS peligrosos

Los analistas de Check Point han advertido que muchos dispositivos Android (incluidos Samsung, Huawei, LG, Sony y posiblemente otros fabricantes) son vulnerables a ataques muy interesantes. Para implementarlos, deberá falsificar un solo mensaje SMS especial, que generalmente proviene de operadores móviles, y un atacante podrá interceptar el correo electrónico o el tráfico de dispositivos vulnerables.

El problema identificado por los expertos está relacionado con las instrucciones de OMA CP (Open Mobile Alliance Client Provisioning). Este es un estándar por el cual los operadores móviles pueden enviar configuraciones de red en forma de mensajes especiales a los dispositivos del cliente. Dichos mensajes pueden contener configuraciones del servidor MMS, dirección de proxy, servidor de correo, página de inicio del navegador y configuraciones de marcadores, servidores para sincronizar contactos y calendario, y mucho más.

Los investigadores descubrieron que cuatro fabricantes de teléfonos inteligentes implementaron este estándar en sus dispositivos de manera insegura. Los teléfonos inteligentes Samsung, Huawei, LG y Sony pueden recibir mensajes OMA CP, incluso si fueron recibidos de una fuente poco confiable.

  
  

[![](https://xakep.ru/wp-content/uploads/2019/10/240935/Capture.png#26759185)](https://xakep.ru/wp-content/uploads/2019/10/240935/Capture.png#26759185)

  

  

La forma más fácil era atacar los dispositivos Samsung, ya que reciben mensajes de OMA CP sin ninguna autenticación o verificación. Los teléfonos inteligentes Huawei, LG y Sony están ligeramente mejor protegidos, ya que, en su caso, el remitente del mensaje debe proporcionar al menos dispositivos IMSI.

Aunque en teoría los códigos IMSI son difíciles de obtener, los expertos explican que nada es imposible. Por ejemplo, los operadores móviles brindan servicios pagos con los que traducen números de teléfono a códigos IMSI para proveedores de servicios móviles de terceros. Es decir, un atacante puede obtener IMSI del proveedor por una pequeña tarifa. Peor aún, casi un tercio de todas las aplicaciones de Android tienen acceso a dispositivos IMSI, ya que solicitaron con éxito los permisos correspondientes. Esto significa que los piratas informáticos pueden usar códigos IMSI obtenidos a través de aplicaciones maliciosas o fugas de datos.

El ataque descrito por Check Point no es automático (el usuario debe presionar un botón y aceptar la instalación de la nueva configuración del atacante), pero los investigadores advierten que los atacantes pueden falsificar fácilmente al remitente. De hecho, el destinatario no tiene una forma real de determinar quién envió el mensaje. Por desgracia, esto significa que muchos usuarios aceptarán cambiar la configuración del dispositivo a una nueva, creyendo que los recibe de un operador móvil real.

Como resultado, al cambiar la configuración, el atacante puede, por ejemplo, redirigir todo el tráfico de la víctima a través de su servidor malicioso. Para implementar tal ataque, no se necesita equipo especial: para enviar un SMS, un módem GSM (un dispositivo USB por diez dólares o un teléfono que funciona en modo módem) y un simple script será suficiente.

  
  

[![Mensaje OMA CP, dividido en dos SMS y que contiene carga útil](https://xakep.ru/wp-content/uploads/2019/10/240935/advanced_05.png#26759185)](https://xakep.ru/wp-content/uploads/2019/10/240935/advanced_05.png#26759185)

Mensaje OMA CP, dividido en dos SMS y que contiene carga útil

  

Afortunadamente, tres de los cuatro fabricantes identificados en el informe ya están trabajando para solucionar este problema:

*   Samsung ha incluido un parche para este problema en el kit de actualización de mayo;
*   LG lanzó su solución en julio;
*   Huawei planea hacer las correcciones de UI necesarias para la próxima generación de teléfonos inteligentes de las series Mate y P.

El único fabricante que no va a solucionar el problema es Sony. Los investigadores explican que los ingenieros de Sony "se negaron a reconocer la vulnerabilidad, diciendo que sus dispositivos cumplen con la especificación OMA CP".

  

Pero los analistas de Check Point no solo recomiendan a los fabricantes que publiquen parches, sino que los usuarios los instalen. En su opinión, los operadores móviles deberían bloquear los mensajes OMA CP a nivel de red para que los mensajes de este tipo no puedan pasar a través de sus redes, a menos que los envíe el propio operador. Según los expertos, en la actualidad, no se puede confiar en absoluto en los mensajes OMA CP, y es mejor rechazarlos a todos.  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2019/10/01/meganews-246/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)