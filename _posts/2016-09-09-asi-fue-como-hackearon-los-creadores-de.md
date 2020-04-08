---
title: 'Así fue como hackearon a los creadores de un ataque vía ransomware'
date: 2019-10-18T04:56:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-UUmDhIrebZw/XanlXel9ZlI/AAAAAAAALJQ/0abe4aKCD8wkOKTa1DaR9LTuOHtp5U5pgCLcBGAsYHQ/s640/ransomware-2315203_960_720.jpg)](https://1.bp.blogspot.com/-UUmDhIrebZw/XanlXel9ZlI/AAAAAAAALJQ/0abe4aKCD8wkOKTa1DaR9LTuOHtp5U5pgCLcBGAsYHQ/s1600/ransomware-2315203_960_720.jpg)

  
Un usuario parece haber encontrado su venganza personal contra una banda que se dedica a crear ransomware, código malévolo que cifra los archivos de la computadora de la víctima y que, para que se puedan recuperar, piden un rescate en bitcoins.

Un hacker de sombrero blanco, es decir, alguien que no busca hacer daño computacionalmente, encontró cómo hackear los servidores de los criminales digitales y consiguió las claves de decodificación para todas las víctimas.

La banda de Mukstik, creadora de un ransomware que ha estado activo desde septiembre pasado, sufrió el ataque a su servidor en donde el hacker se hizo de las contraseñas que pueden ayudar a recrear los archivos cifrados.

Normalmente el cifrado es imposible de descifrar a prueba de error (podría llevar miles de años), por lo que este archivo encontrado por el hacker bueno, es una gran noticia.

**[El ransomware de Mukstik](https://www.zdnet.com/article/white-hat-hacks-muhstik-ransomware-gang-and-releases-decryption-keys/)** ataca lo dispositivos con almacenamiento en la red (NAS por sus siglas en inglés), creado por el vendedor de hardware de Taiwan, QNAP.

La banda de criminales cibernéticos usan un esquema de fuerza bruta para hallar las contraseñas en el servicio interconstruido _phpMyAdmin_, de acuerdo con un consejero de seguridad, el cual publicó información acerca de este ransomware.

Después de lograr el acceso a la instalación de phpMyAdmin, los operadores de Muhstik cifran los archivos de los usuarios y guardan una copia de las claves de descifrado en su servidor de_ comando y control_ (C&C). Los archivos codificados tienen una nueva extensión llamada «._muhstik_«.

Una de las víctimas de este ataque fue Tobias Frömel, un programador alemán. Frömel fue de los quienes pagaron la cifra pedida por los ladrones para obtener acceso a sus archivos cifrados.

Una vez pagada la cantidad pedida, Frömel analizó el ransomware y logró entender cómo operaba Muhstik. De esta manera logró hacerse de la base de datos del servidor de los malvados personajes.

> «Lo sé, no fue algo legal lo que hice», indica Frömel, que publicó un archivo en **[pastebin](https://pastebin.com/raw/N8ahWBni)**, conteniendo un total de 2,858 llaves de decodificación, «pero yo no soy el malo aquí». agregó Frömel.

Ayuda solidaria
---------------

Cabe señalar que, además de las claves de descifrado publicadas, el desarrollador alemán publicó un sistema de decodificación que puede ser usado por cualquier víctima de este ransomware. El descifrador está en este **[sitio](https://mega.nz/#!O9Jg3QYZ!5Gj8VrBXl4ebp_MaPDPE7JpzqdUaeUa5m9kL5fEmkVs)**, junto con sus instrucciones.

Frömel entonces se decidió anunciar a las víctimas de Muhstick en Twitter, sobre la disponibilidad de su herramienta y pidiendo a las víctimas que no paguen ningún dinero para recuperar sus archivos.

Frömel también dio aviso a las autoridades que ya están buscando a estos hackers a partir de sus huellas digitales. Ojalá y que esto sera un aviso de que el crimen no paga.

Hay quien piensa que las acciones de Frömel no fueron legales, pero es poco probable que los de la banda del ransomware decidan acusarlo legalmente de algo. En cualquier caso, los investigadores en el tema de seguridad aconsejan trabajar con las autoridades para evitar potenciales problemas legales.  
  

Fuente: [https://www.unocero.com/](https://www.unocero.com/seguridad/hackeo-ransomware/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)