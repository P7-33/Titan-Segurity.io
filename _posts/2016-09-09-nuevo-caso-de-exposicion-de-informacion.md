---
title: 'Nuevo caso de exposición de información personal afecta a más de 2
millones de colombianos'
date: 2019-11-05T03:58:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-1tp6X74KFC0/XcDlTT6tEaI/AAAAAAAALOk/hdaMRpVxpSQBYWeFeo_SWk8fy6ma_--HgCLcBGAsYHQ/s640/colombia-1460312_960_720.jpg)](https://1.bp.blogspot.com/-1tp6X74KFC0/XcDlTT6tEaI/AAAAAAAALOk/hdaMRpVxpSQBYWeFeo_SWk8fy6ma_--HgCLcBGAsYHQ/s1600/colombia-1460312_960_720.jpg)

  
Un nuevo caso de una base de datos mal configurada deja expuesta información personal de usuarios de Colombia y evidencia la falta de consideración de aspectos de seguridad desde el diseño.

  

Después de que saliera a la luz la noticia de la [masiva cantidad de datos expuestos por una empresa en Ecuador](https://www.welivesecurity.com/la-es/2019/09/18/mala-gestion-datos-empresas-consecuencias/) como consecuencia de una base de datos mal configurada, como profesional que trabaja en temas de seguridad informática tenía la esperanza de que el caso pudiera servir de aprendizaje para que las empresas en Latinoamérica comenzaran un proceso de verificación de sus implementaciones para asegurarse de no tener expuesta su información; pero al parecer, esto no pasó.

  

Esta misma esperanza fue la que me llevó a pensar, después de los incidentes de Wannacry, hace ya más de dos años, que las empresas iban a corregir las vulnerabilidades en SMB actualizando sus sistemas operativos, pero al día de hoy [seguimos viendo detecciones del exploit EternalBlue](https://www.welivesecurity.com/la-es/2019/05/17/detecciones-eternalblue-alcanza-nuevo-pico-desde-wannacry/). Entonces, ¿están las empresas pensando en la seguridad de la información desde el diseño de sus proyectos?

### **Colombia y un reciente caso de exposición de información personal de más de 2 millones de personas**

Hace una semanas, fuimos contactados por el equipo de [The Hack](https://thehack.com.br/exclusivo-empresa-colombiana-expoe-mais-de-2-4-milhoes-de-registros-pessoais/) por lo que parecían ser datos de ciudadanos colombianos expuestos en Internet. Luego de algunas verificaciones, corroboramos que se trataba de una instancia de ElasticSearch configurada de manera insegura que estaba dejando expuesta en Internet información de más de 2.4 millones de usuarios de este país, sin necesidad de autenticación. Parte de esa información estaba compuesta por nombre, dirección de correo, número de teléfono y número de cédula.

[![](https://www.welivesecurity.com/wp-content/uploads/2019/10/CantidadDeDatosFIltrados.jpg)](https://www.welivesecurity.com/wp-content/uploads/2019/10/CantidadDeDatosFIltrados.jpg)  

Captura de pantalla donde se aprecia la cantidad de usuarios afectados y parte de los datos expuestos.

Así que, a partir de ese momento, el objetivo fue contactar a diferentes entidades en Colombia para intentar identificar qué empresa estaba teniendo el problema y poder notificarle para evitar que la información continuara expuesta. Esta fue probablemente la tarea que más tiempo nos llevó. Mientras más tiempo transcurría intentando comunicarnos con las personas adecuadas dentro de cada organización para que nos ayudara a solucionar el problema; los datos continuaban estando públicos. Por suerte, el problema se corrigió y la información ya no está expuesta.

  

Este incidente deja en evidencia, nuevamente, que las empresas aún no están considerando la seguridad de los datos desde el diseño de sus implementaciones. Una tecnología será tan segura como el tiempo que se le dedique para hacerla segura.

  

Los casos recientes de instancias de ElasticSearch en empresas de países de Lationamérica deberían servir de alerta para que todas aquellas empresas que utilizan esta tecnología se tomen un tiempo para verificar el estado de seguridad de sus implementaciones. Sobre todo si tenemos en cuenta que el acceso indebido a la información y el robo de la misma son dos de las principales preocupaciones de las empresas en América Latina, según datos de la edición 2019 del [ESET Security Report](https://www.welivesecurity.com/wp-content/uploads/2019/07/ESET-security-report-LATAM-2019.pdf).

  

Después de este tipo de hallazgos y la trascendencia pública que adquieren, lo lógico debería ser que una disminución de casos como estos. Más allá de lo negativo que puede resultar tener estas tecnologías expuestas, debería tomarse como positivo el conocer cuáles son las posibles vulnerabilidades y corregirlas para que algo así no siga ocurriendo.

  

Cuando se habla de información personal de los usuarios, las empresas deben garantizar su seguridad por encima de la funcionalidad y la usabilidad de las aplicaciones o servicios. Los recientes casos de implementaciones inadecuadas de tecnologías como ElasticSearch que hemos visto en [Ecuador](https://www.welivesecurity.com/la-es/2019/09/18/mala-gestion-datos-empresas-consecuencias/), [Brasil](https://thehack.com.br/exclusivo-mcdonalds-deixa-vazar-dados-de-mais-de-1-milhao-de-funcionarios-brasileiros/), y ahora en Colombia, dejan en evidencia que muchas veces las organizaciones priorizan su negocio sobre la seguridad de la información. Sin embargo, este tipo de incidentes deben servir como lecciones para que las empresas dediquen tiempo y asignen los recursos necesarios para revisar sus tecnologías y hacer de la seguridad un proceso continuo que atraviese todas las operaciones del negocio. De lo contrario, no solo estarán expuestas a que les ocurra algo similar, sino a las consecuencias que conlleva ser responsable de un incidente de esta naturaleza.

  

Más allá de los incumplimientos normativos que implica este tipo de incidentes, las empresas deben considerar que sus clientes y usuarios pueden quedar expuestos a una amplia variedad de ataques de ingeniería social dirigidos en el caso que esta información caiga en manos inadecuadas.

  

Este caso esperemos sirva como recordatorio de lo importante que es que las empresas evalúen sus sistemas de información y cómo están configurados. La implementación de una tecnología que aporte las herramientas para desarrollar las actividades operativas, como en este caso es ElasticSearch, no debe perder de vista la necesidad de revisar que cuente con las configuraciones adecuadas para no dejar expuesta la información que con ellas se maneja. Todos estos incidentes nos recuerdan la importancia de pensar en seguridad desde el inicio de cualquier proyecto.  
  

Fuente: [https://www.welivesecurity.com/](https://www.welivesecurity.com/la-es/2019/10/29/exposicion-informacion-personal-afecta-millones-colombianos/)

No olvides Compartir...

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)