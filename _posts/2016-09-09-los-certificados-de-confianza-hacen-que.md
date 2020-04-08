---
title: 'Los certificados de confianza hacen que los sitios web de phishing
parezcan válidos'
date: 2019-11-18T15:02:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-i9uaza5IlZw/XdKjwqDe6OI/AAAAAAAALWA/4nYhhJLG-MEoK5wUELQXyNFkS2w8v0f-gCLcBGAsYHQ/s640/https-3344700_960_720.jpg)](https://1.bp.blogspot.com/-i9uaza5IlZw/XdKjwqDe6OI/AAAAAAAALWA/4nYhhJLG-MEoK5wUELQXyNFkS2w8v0f-gCLcBGAsYHQ/s1600/https-3344700_960_720.jpg)

  

Ha habido un crecimiento desenfrenado de dominios similares, que a menudo se utilizan para robar datos confidenciales de los compradores en línea.  
  

Venafi analizó dominios sospechosos dirigidos a 20 minoristas principales en los EE. UU., Reino Unido, Francia, Alemania y Australia y encontró más de 100,000 dominios similares que usan certificados TLS válidos para parecer seguros y confiables.

  

Según la investigación, el crecimiento en el número de dominios similares se ha más que duplicado desde 2018, superando a los dominios legítimos en casi cuatro veces.

**Resultados clave**

  

El número total de certificados utilizados en dominios similares es más de un 400% mayor que el número de dominios minoristas auténticos.

  

Los principales minoristas son objetivos importantes para los ciberdelincuentes.   
  
Uno de los principales minoristas de EE. UU. Tiene más de 49,500 dominios similares que se dirigen a sus clientes.

  

Hay más de seis veces más dominios parecidos que dominios válidos entre los 20 principales minoristas en línea del Reino Unido.

  

Más de la mitad (60%) de los dominios parecidos estudiados usan certificados gratuitos de Let’s Encrypt.

  

A medida que las compras en línea continúan creciendo, también lo hace la focalización de los consumidores a través de dominios similares maliciosos. Los atacantes cibernéticos crean dominios fraudulentos al sustituir algunos caracteres en las URL.

  

Debido a que apuntan a sitios web de compras en línea maliciosos que imitan estrechamente a sitios web minoristas legítimos y conocidos, dificulta cada vez más a los clientes detectar los dominios falsos.

  

Además, dado que muchas de estas páginas maliciosas usan un certificado TLS confiable, parecen ser seguras para los compradores en línea que, sin saberlo, brindan información confidencial de la cuenta y datos de pago.

**Pasos de protección para minoristas en línea**

  

A medida que se acerca la temporada de compras navideñas, se multiplicará la cantidad de dominios similares que se dirigen a los compradores en línea. Los minoristas en línea que descubren dominios maliciosos pueden tomar varias medidas para proteger a sus clientes, que incluyen:

  

Busque e informe dominios sospechosos con [Google Safe Browsing](https://safebrowsing.google.com/). Google Safe Browsing es un servicio anti-phishing de la industria que identifica y pone en la lista negra sitios web peligrosos.

  

Agregue la Autorización de autoridad de certificación ([CAA](https://letsencrypt.org/docs/caa/)) a los registros DNS de dominios y subdominios. CAA permite a las organizaciones determinar qué CA pueden emitir certificados para los dominios que poseen. Es una extensión del registro DNS del dominio y admite etiquetas de propiedad que permiten a los propietarios establecer la política de CA para dominios completos o para nombres de host específicos.

  

Aproveche las soluciones tecnológicas para buscar dominios sospechosos. Los servicios de protección de marca pueden ayudar a los minoristas a encontrar sitios web maliciosos y detener el uso no autorizado de sus logotipos o marcas. Las soluciones que también proporcionan funcionalidad anti-phishing pueden ayudar a ayudar en la búsqueda de dominios similares.

  

Detecta certificados maliciosos con la Transparencia de certificados. Todas las identidades de máquina de confianza pública, como los certificados TLS, se publican en registros abiertos. Monitorear y analizar estos registros permite a las organizaciones detectar dominios y certificados similares antes de que se usen en ataques contra clientes.

  

"Continuamos viendo un crecimiento desenfrenado en la cantidad de dominios parecidos peligrosos utilizados en ataques de phishing depredadores", dijo Jing Xie, investigador de inteligencia de amenazas de [Venafi](https://www.helpnetsecurity.com/tag/venafi/).

  

"Este es el resultado del impulso para cifrar más y potencialmente todo el tráfico web, una tendencia que generalmente mejora la seguridad de los usuarios, pero sin darse cuenta presenta un nuevo desafío a los métodos existentes de detección de phishing. La mayoría de las empresas y muchos minoristas no cuentan con la tecnología actualizada para encontrar estos sitios maliciosos y eliminarlos para proteger a sus clientes ".  
  
  

Fuente: [https://www.helpnetsecurity.com/](https://www.helpnetsecurity.com/2019/11/18/dangerous-look-alike-domains/)

No olvides Compartir...

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)