---
title: 'Hera v2.6.5 – Creative Multipurpose WordPress Theme'
date: 2020-01-07T11:37:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
Dentro de los procesos de seguridad, tanto ofensivos como defensivos, es muy importante el trabajar con diccionarios y wordlist para fuerza bruta.  
  
Espera, de manera defensiva? comorrrrrr !!!! Espero que hayas leído el artículo sobre [como usar las listas de passwords de manera defensiva del anterior artículo](https://kinomakino.blogspot.com/2020/01/blue-team-auto-fuerza-bruteate-active.html)...  
  
Pero en esta ocasión vamos a centrarnos en la parte de generación de diccionarios, independientemente del uso que le des. En este blog hemos hablado hace años de herramientas como [CUPP](https://kinomakino.blogspot.com/2012/09/cupp-common-user-passwords-profiler.html),  [Crunch](https://kinomakino.blogspot.com/2012/10/crunchchocholate-y-claves.html), [ThaDoctor](https://kinomakino.blogspot.com/2012/10/asistente-de-creacion-de-wordlist.html), [who´s your daddy](https://kinomakino.blogspot.com/2012/09/whos-your-daddy-creacion-de-wordlist.html), [CEWL](https://kinomakino.blogspot.com/2012/07/diccionarios-mutaciones-cewl-rsmangler.html)  y en esta ocasión voy a comentar una sencilla herramienta para el mismo propósito, pero muy sencilla y gráfica. [The Mentalist.](https://github.com/sc0tfree/mentalist)  
  

[![](https://1.bp.blogspot.com/-oVxU5iFfSK4/XhHuH_smW8I/AAAAAAAAGdk/PjLXMgqdbpQGSkr_OxgfWHJc8Y0jtCsQgCLcBGAsYHQ/s1600/68747470733a2f2f73633074667265652e73717561726573706163652e636f6d2f732f4d656e74616c6973742d6c6f676f2d32353070782e706e67.png)](https://1.bp.blogspot.com/-oVxU5iFfSK4/XhHuH_smW8I/AAAAAAAAGdk/PjLXMgqdbpQGSkr_OxgfWHJc8Y0jtCsQgCLcBGAsYHQ/s1600/68747470733a2f2f73633074667265652e73717561726573706163652e636f6d2f732f4d656e74616c6973742d6c6f676f2d32353070782e706e67.png)

  
El uso es muy sencillo, es más es casi block chain !! jajajaja, usa chains, cadenas, en las que voy construyendo "condiciones" o casos sobre el texto.  
  
La primera chain es el "input", el texto. aquí por ejemplo podríamos poner el nombre de la empresa, informático, producto, sector,etc, y podemos poner varios.  
  
En el siguiente chain, vamos a realizar una modificación de mayúsculas/minúsculas con varios criterios.  
  
Los chains son muy sencillos y donde mejor explicado está es en la propia documentación. Por ejemplo...  
  

Attribute

Description

No Words

Provides an empty string

Custom File...

User-specified custom wordlist file

Custom String...

User-specified custom string

English Dictionary

English dictionary taken from the Unix `words` file

Common Names

 Men

1,000 most common mens' names in the US

 Women

1,000 most common womens' names in the US

 Pets

1,200 most common pets' names in the US

Other

 Slang & Expletives

Wordlist of US slang and expletives

 Months & Seasons

Wordlist of months and seasons

  
Tiene opciones sencillas, como el típico de añadir años antes o después de la palabra, poner la primera letra en mayúsculas, c4mb1ar las letras a lo hacker, etc...  
  

[![](https://1.bp.blogspot.com/-W3sJwomd5kY/XhHvHK0mivI/AAAAAAAAGdw/XLQ5TIfUD1M-EK8IDIx-gfRQbTC456XhgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-04%2Ba%2Blas%2B22.45.38.png)](https://1.bp.blogspot.com/-W3sJwomd5kY/XhHvHK0mivI/AAAAAAAAGdw/XLQ5TIfUD1M-EK8IDIx-gfRQbTC456XhgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-04%2Ba%2Blas%2B22.45.38.png)

  

[![](https://1.bp.blogspot.com/-uHtlQOyu94A/XhHvHMDwt-I/AAAAAAAAGds/jBWGk08SX7oz9Lk2ougOtoM0fT6PkTXQwCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-04%2Ba%2Blas%2B22.45.53.png)](https://1.bp.blogspot.com/-uHtlQOyu94A/XhHvHMDwt-I/AAAAAAAAGds/jBWGk08SX7oz9Lk2ougOtoM0fT6PkTXQwCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-04%2Ba%2Blas%2B22.45.53.png)

  
Una herramienta más que anidad con otras, puede que nos ayude a crear un diccionario personalizado interesante para nuestros fines.  
  
Espero que os guste !!!