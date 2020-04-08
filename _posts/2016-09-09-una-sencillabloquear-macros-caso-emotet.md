---
title: 'Una sencilla...bloquear Macros... Caso Emotet'
date: 2019-10-07T11:08:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
Hace ya unas semanas que llevamos sufriendo una oleada de ataques del troyano tipo Emotet.  
  
Sin entrar en detalles, es un malware que por lo general esconde un dropper, un programa malicioso que se descarga el auténtico "bicho" del malware. En esta ocasión un troyano bancario con el fin de intentar obtener claves y envirular al resto de mortales y conocidos mediante una propagación basada en contactos del correo. Hay mil artículos al respecto mejor explicados que yo.  
  

[![](http://www.asnet.es/blog/wp-content/uploads/2019/09/ALERTA-800x800.jpg)](http://www.asnet.es/blog/wp-content/uploads/2019/09/ALERTA-800x800.jpg)

  
Lo que estamos aconsejando en los centros de operaciones y empresas prestadoras a nuestros clientes es que bloqueen por defecto el uso de Macros en los documentos de ofimática.  
  
Esto suscita muchos impedimentos, ya que muchas empresas usan ficheros, sobre todo Excel, para realizar pequeños ( o grandes) procesos de negocio y usarlos como base para pintar dashboards, informes y cosas así.  
  
Al final es una función muy interesante de la ofimática, pero que por desgracia está siendo empleada como mecanismo de evasión de antivirus para realizar las maldades de los cibercriminales.  
  
Mi pequeño consejo quizás lo conozcas, pero mucha gente no. Estamos hablando de soluciones de hace 20 años...  
  
Usar Gpo !!! si !! las políticas de grupo de toda la vida. Hay plantillas administrativas, las ADMX de muchos productos, que nos permiten configurar mediante Group Policies de dominio ciertos aspectos de software de terceros, no solo del sistema operativo. Para el caso de Office 2016 podemos descargarlas desde [aquí](https://www.microsoft.com/en-us/download/details.aspx?id=49030).  
  
Pero como te digo, hay plantillas administrativas para mucho software comercial, por ejemplo, [Firefox.](https://github.com/mozilla/policy-templates/releases)  
  
Bueno seguimos, una vez tenemos el fichero ADMX descargado, copiamos el contenido de las plantillas a c:\\windows\\policydefinitions\\ y ya las tenemos disponibles en el editor de directivas de grupo.  
  
Aquí cabe la pena hacer un inciso. Vamos a bloquear el uso de macros en ficheros Word por ejemplo, pero vamos a establecer unas zonas de confianza o trusted zones para que los usuarios SI puedan ejecutar macros en ficheros Word de esa ubicación.  
  
Es una buena medida de seguridad que permite cierta usabilidad.  
  
El proceso es muy sencillo.  
  

[![](https://1.bp.blogspot.com/-NjepPt2k6bQ/XZr_QQT7IPI/AAAAAAAAGZA/LSkGGrbAO1sEsaDijVvedKcVGnZ7I0pmACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B10.57.55.png)](https://1.bp.blogspot.com/-NjepPt2k6bQ/XZr_QQT7IPI/AAAAAAAAGZA/LSkGGrbAO1sEsaDijVvedKcVGnZ7I0pmACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B10.57.55.png)

  

[![](https://1.bp.blogspot.com/-BASi83OnSi0/XZr_QfCjbDI/AAAAAAAAGY8/ZCMQKhLEongB6Ho1mmyoX86dYRYxzSjFQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B10.59.20.png)](https://1.bp.blogspot.com/-BASi83OnSi0/XZr_QfCjbDI/AAAAAAAAGY8/ZCMQKhLEongB6Ho1mmyoX86dYRYxzSjFQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B10.59.20.png)

  
Otro consejo para los más iniciados en el ámbito de la ciberseguridad, es que conociendo este "comodín" para hacer un "bypass" del bloque de macros, es común que el malware intente alterar esa rama del registro para dotar de "zona de confianza" al fichero.  
  
Muy recomendable monitorizar los cambios de la siguiente rama del registro.  
  
HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\16.0\\Word\\Security\\Trusted Locations  
  
  
Espero que os sirva, gracias por leerme !!!