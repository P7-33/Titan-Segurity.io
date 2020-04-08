---
title: 'Microsoft Security Compliance KIT'
date: 2019-10-24T18:39:00+01:00
draft: false
---

Estimados amigos de inseguros !!!!  
  
En la entrega de hoy voy a comentar algo que lleva tiempo rulando por los sistemas de la compañía de Seattle pero que no había documentado por aquí, el [Ms. Security Compliance Kit](https://docs.microsoft.com/es-es/windows/security/threat-protection/security-compliance-toolkit-10).  
  

[![](https://1.bp.blogspot.com/-_QC1FsaiyCQ/XbHhtnCc_QI/AAAAAAAAGck/bULV7q2Y0y8Os0nOd4UHVB6XzgsL9qPhACLcBGAsYHQ/s320/34dc348757fb77da3c6412990dd96af9f29ac8ae25678a1e7c4d3ca8b8c8aebf.jpg)](https://1.bp.blogspot.com/-_QC1FsaiyCQ/XbHhtnCc_QI/AAAAAAAAGck/bULV7q2Y0y8Os0nOd4UHVB6XzgsL9qPhACLcBGAsYHQ/s1600/34dc348757fb77da3c6412990dd96af9f29ac8ae25678a1e7c4d3ca8b8c8aebf.jpg)

  
Como puedes apreciar en la descripción, es un kit de herramientas que te permiten realizar una auditoría de cumplimiento de tus estándares de seguridad, es decir, si estás aplicando bien las políticas que crees que estás aplicando.  
  
Es un producto gratuito disponible para sistemas operativos > 2012r2.  
  
En esta prueba vamos a "ejecutarlo" sobre un Dc Windows Server 2019....  
  
Lo primero que voy a hacer es ver la documentación, un fichero excel con las configuraciones que me recomienda para cada versión de sistema operativo y su role.  
  

[![](https://1.bp.blogspot.com/-Oe-etrwibFA/XbCc43qnyLI/AAAAAAAAGbo/XTVgn6luescMjvvd-YcqtNirbHoF7YQyACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.01.48.png)](https://1.bp.blogspot.com/-Oe-etrwibFA/XbCc43qnyLI/AAAAAAAAGbo/XTVgn6luescMjvvd-YcqtNirbHoF7YQyACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.01.48.png)

  
Puede que estés contento con el resultado que te proponen, pero revisalo muy bien.  
  
Es momento de irnos al editor de directivas de grupo y crear una, darle a importar, e importar el setting que nos corresponde. Sencillo !!!  
  

[![](https://1.bp.blogspot.com/-n5KnQUfGf6U/XbCdRGYSosI/AAAAAAAAGb0/rTW6S8sdHBoJoNL8Vbl_SrpFXUKtvM4FwCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.03.png)](https://1.bp.blogspot.com/-n5KnQUfGf6U/XbCdRGYSosI/AAAAAAAAGb0/rTW6S8sdHBoJoNL8Vbl_SrpFXUKtvM4FwCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.03.png)

  

[![](https://1.bp.blogspot.com/-cg5vW7JEDBc/XbCdRAL-W8I/AAAAAAAAGbw/LpP8-wI3UDAhN4JHyRNdMlnXVsnC7YyaACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.09.png)](https://1.bp.blogspot.com/-cg5vW7JEDBc/XbCdRAL-W8I/AAAAAAAAGbw/LpP8-wI3UDAhN4JHyRNdMlnXVsnC7YyaACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.09.png)

  

[![](https://1.bp.blogspot.com/-4w_DB-V7amQ/XbCdRLwwEBI/AAAAAAAAGb4/NGO4uwuUdt4xlVEzev_7dFOsCb9Ha0BFgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.19.png)](https://1.bp.blogspot.com/-4w_DB-V7amQ/XbCdRLwwEBI/AAAAAAAAGb4/NGO4uwuUdt4xlVEzev_7dFOsCb9Ha0BFgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.27.19.png)

  

[![](https://1.bp.blogspot.com/-lfb0fkjtFIc/XbCdRu1r-QI/AAAAAAAAGb8/WbETIiX5maY0k7qnOlDJsIGpIumAX8ujgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.28.26.png)](https://1.bp.blogspot.com/-lfb0fkjtFIc/XbCdRu1r-QI/AAAAAAAAGb8/WbETIiX5maY0k7qnOlDJsIGpIumAX8ujgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-23%2Ba%2Blas%2B20.28.26.png)

  
Con este proceso tenemos cargadas ( que no linkadas a ningún objeto) las directivas de grupo por defecto que Ms nos recomienda...  
  
Pero seguro que esto te da rollo, a mi me lo da. Mejor será tener una herramienta por ejemplo, Policy Analyzer dentro del kit, que le pases varias GPO´s, y te muestre en amarillo los cambios puntuales, para re-comprobar qué estás cambiando...  
  

[![](https://1.bp.blogspot.com/-Z2o9tz-gNnY/XbHfkgEEefI/AAAAAAAAGcU/QRa8c_FkdIAOTpaLUwV3kYYvESoOiyGdgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-24%2Ba%2Blas%2B19.16.38.png)](https://1.bp.blogspot.com/-Z2o9tz-gNnY/XbHfkgEEefI/AAAAAAAAGcU/QRa8c_FkdIAOTpaLUwV3kYYvESoOiyGdgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-24%2Ba%2Blas%2B19.16.38.png)

  

[![](https://1.bp.blogspot.com/-8Yx5VrkyRDE/XbHfkV1IIoI/AAAAAAAAGcQ/CsgPWoYEhKA4creltAVxS4IFwG8dgJsQACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-24%2Ba%2Blas%2B19.16.51.png)](https://1.bp.blogspot.com/-8Yx5VrkyRDE/XbHfkV1IIoI/AAAAAAAAGcQ/CsgPWoYEhKA4creltAVxS4IFwG8dgJsQACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-24%2Ba%2Blas%2B19.16.51.png)

  
Interesante eh !! te puedes animar a cargar tu GPO, la deseada, y puntualmente cargar los elementos uno a uno según te interese. Yo lo haría así !!!  
  
Microsoft ha pensado en todo, y tienes otra herramienta en el kit denominada LGPO para el manejo de las GPO por líneas de comandos, para los equipos fuera del dominio... para cargar, exportar, guardar configuraciones, también muy interesante.  
  
Espero que os guste y os quite el miedo de usar estas herramientas y fortificar los servidores y equipos.  
  
Atentos a la próxima entrada que promete un premio xDDD  
  
Gracias por leerme