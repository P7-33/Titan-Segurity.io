---
title: '250 millones de registros de soporte al cliente de Microsoft expuestos
en línea'
date: 2020-01-23T21:17:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-mQsk71yu2uw/Xin_UgANtmI/AAAAAAAALq4/TyqCBhpTDpg47kPALhuaNWA5awGPDKsAACLcBGAsYHQ/s640/microsoft-customer-support-min.jpg)](https://1.bp.blogspot.com/-mQsk71yu2uw/Xin_UgANtmI/AAAAAAAALq4/TyqCBhpTDpg47kPALhuaNWA5awGPDKsAACLcBGAsYHQ/s1600/microsoft-customer-support-min.jpg)

  
Si alguna vez ha contactado con Microsoft para obtener asistencia en los últimos 14 años, su consulta técnica, junto con alguna información de identificación personal, podría haberse visto comprometida.

  

Microsoft admitió hoy un incidente de seguridad que expuso casi 250 millones de registros de "Servicio y soporte al cliente" (CSS) en Internet debido a un servidor mal configurado que contiene registros de conversaciones entre su equipo de soporte y los clientes.

  

Según Bob Diachenko, un investigador de seguridad cibernética que detectó la base de datos desprotegida e informó a Microsoft, los registros contenían registros que abarcaban desde 2005 hasta diciembre de 2019.

  

En una publicación de blog, Microsoft confirmó que debido a las reglas de seguridad mal configuradas agregadas al servidor en cuestión el 5 de diciembre de 2019, permitió la exposición de los datos, que se mantuvo igual hasta que los ingenieros remediaron la configuración el 31 de diciembre de 2019.

  

Microsoft también dijo que la base de datos fue redactada utilizando herramientas automatizadas para eliminar la información de identificación personal de la mayoría de los clientes, excepto en algunos escenarios donde la información no era el formato estándar.

  

"Nuestra investigación confirmó que la gran mayoría de los registros se borraron de información personal de acuerdo con nuestras prácticas estándar", dijo Microsoft.

  

Sin embargo, según Diachenko, muchos registros en la base de datos filtrada contenían datos legibles sobre los clientes, incluidos sus:

*   correos electrónicos,
*   Direcciones IP,
*   Ubicaciones,
*   Descripciones de reclamos y casos de CSS,
*   Correos electrónicos del agente de soporte de Microsoft,
*   Números de casos, resoluciones y comentarios,
*   Notas internas marcadas como "confidenciales".

  

"Este problema era específico de una base de datos interna utilizada para el análisis de casos de soporte y no representa una exposición de nuestros servicios comerciales en la nube", dijo Microsoft.

  

Al tener a mano la información sensible del caso y las direcciones de correo electrónico de los clientes afectados, los estafadores de soporte técnico podrían abusar de los datos filtrados para engañar a los usuarios para que paguen por problemas informáticos inexistentes haciéndose pasar por representantes de soporte de Microsoft.

  

"La ausencia de información de identificación personal es irrelevante aquí, dado que los registros de soporte técnico con frecuencia exponen a los clientes VIP, sus sistemas internos y configuraciones de red, e incluso contraseñas. Los datos son una mina de oro para los delincuentes pacientes con el objetivo de violar organizaciones grandes y gobiernos ", dijo el director de operaciones de ImmuniWeb Ekaterina Khrustaleva a The Hacker News.

  

"Peor aún, muchas grandes empresas y no solo Microsoft han perdido la visibilidad de su superficie de ataque externo, exponiendo a sus clientes y socios a riesgos significativos. Probablemente veremos una multitud de incidentes similares en 2020".

  

Roger Grimes, también compartió su comentario y experiencia con The Hacker News, diciendo:

  

"Después de haber trabajado para Microsoft durante 15 años, 11 años como empleado a tiempo completo, he visto de primera mano cuánto tratan de luchar en escenarios como este. Hay múltiples niveles de controles y educación diseñados para evitar que suceda. Y muestra lo difícil que es evitarlo el 100% del tiempo. Nada es perfecto. Suceden errores y fugas. Cada organización tiene políticas excesivamente permisivas. Todo! Es solo cuestión de si alguien fuera de la organización lo descubre o si alguien se aprovecha de eso ".

  

"En este caso, por malo que sea, fue descubierto por alguien que no hizo cosas maliciosas con él. Claro, los datos, sin protección, también podrían haber sido utilizados por los malos, pero hasta ahora, nadie ha presentado ese caso o ha aportado pruebas de que se ha utilizado con malicia ", agregó Grimes.

  

"Cualquiera puede cometer un error. La pregunta más importante es cómo ocurrió el error y cómo evitar que ocurra la próxima vez, y si otros pudieron haber ocurrido en el mismo conjunto de circunstancias".

  

  

Como resultado de este incidente, la compañía dijo que comenzó a notificar a los clientes afectados cuyos datos estaban presentes en la base de datos expuesta de Servicio y Atención al Cliente.

  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2020/01/microsoft-customer-support.html)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)