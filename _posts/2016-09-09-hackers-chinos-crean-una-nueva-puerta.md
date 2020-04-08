---
title: 'Hackers chinos crean una nueva puerta trasera para servidores MSSQL'
date: 2019-10-23T23:56:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-pu6kSlsg6Cc/XbDafo7WdOI/AAAAAAAALLY/6Z5fZp1blmEYMsFHUOHeJJQ9oi4DiKnpgCLcBGAsYHQ/s400/server-2891812_960_720.jpg)](https://1.bp.blogspot.com/-pu6kSlsg6Cc/XbDafo7WdOI/AAAAAAAALLY/6Z5fZp1blmEYMsFHUOHeJJQ9oi4DiKnpgCLcBGAsYHQ/s1600/server-2891812_960_720.jpg)

  

Los especialistas de ESET [descubrieron un](https://www.welivesecurity.com/2019/10/21/winnti-group-skip2-0-microsoft-sql-server-backdoor/) nuevo malware creado por intrusos chinos del grupo Winnti y diseñado para realizar cambios en las bases de datos de Microsoft SQL Server (MSSQL) para crear una puerta trasera. Como beneficio adicional, una puerta trasera oculta las sesiones en los registros de conexión de la base de datos cada vez que los hackers usan una "contraseña mágica", que ayuda a los atacantes a pasar desapercibidos.

La herramienta se llama skip-2.0 y está destinada a modificar las funciones MSSQL que son responsables del procesamiento de autenticación. Los atacantes implementan una puerta trasera después de comprometer sus objetivos de otras maneras, ya que la instalación de privilegios requiere privilegios administrativos. De hecho, la herramienta se utiliza para aumentar el sigilo y crear una presencia sostenible.

La idea básica detrás de skip-2.0 es crear la "contraseña mágica" mencionada anteriormente. Si se ingresa dicha contraseña en cualquier sesión de autenticación, el usuario obtiene acceso automáticamente, mientras que las funciones habituales de registro y auditoría no funcionan, lo que resulta en una sesión fantasma que no se ha tenido en cuenta en ningún lado.

  

[![](https://1.bp.blogspot.com/-bv6Xsn2_ZNc/XbDaGSSbTBI/AAAAAAAALLQ/c4NWtyezIMglNZA_O7SeWPJSNpDs0gy-wCLcBGAsYHQ/s320/skip-2_0-injection.png)](https://1.bp.blogspot.com/-bv6Xsn2_ZNc/XbDaGSSbTBI/AAAAAAAALLQ/c4NWtyezIMglNZA_O7SeWPJSNpDs0gy-wCLcBGAsYHQ/s1600/skip-2_0-injection.png)

  

Según los expertos, skip-2.0 solo funciona con los servidores MSSQL versiones 12 y 11. Y aunque MSSQL Server 12 se lanzó en 2014, según Censys, esta versión es la más utilizada.

Durante el análisis del código skip-2.0, los expertos descubrieron evidencia que lo conecta con otras herramientas de Winnti, en particular con las puertas traseras PortReuse y ShadowPad. [PortReuse](https://www.welivesecurity.com/2019/10/14/connecting-dots-exposing-arsenal-methods-winnti/)  es una puerta trasera para servidores IIS descubierta por ESET en redes comprometidas de proveedores de hardware y software en el sur de Asia a principios de este año. [ShadowPad es un](https://securelist.com/shadowpad-in-corporate-networks/81432/)  troyano de puerta trasera de [Windows ](https://securelist.com/shadowpad-in-corporate-networks/81432/)[visto por](https://securelist.com/shadowpad-in-corporate-networks/81432/) primera  [vez](https://securelist.com/shadowpad-in-corporate-networks/81432/)  dentro de las aplicaciones creadas por el fabricante de software surcoreano NetSarang cuando los hackers chinos irrumpieron en su infraestructura a mediados de 2017.

> "Tal puerta trasera puede permitir a los atacantes copiar, modificar o eliminar en secreto el contenido de las bases de datos. Esto puede usarse, por ejemplo, para manipular monedas en el juego para obtener beneficios financieros ”, escriben los expertos de ESET.

Manipulaciones similares con monedas en el juego ya se [informaron](https://xakep.ru/2019/03/12/winnti/) a principios de este año, y los especialistas de FireEye luego [asociaron](https://content.fireeye.com/apt-41/rpt-apt41/) estos ataques con APT41.  
  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2019/10/22/skip-2-0/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)