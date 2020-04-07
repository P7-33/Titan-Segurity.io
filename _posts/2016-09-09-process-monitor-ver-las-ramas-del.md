---
title: 'Process Monitor. Ver las ramas del registro que se crean al hacer
settings en Windows.'
date: 2020-01-15T18:20:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!

  

En el episodio de hoy vamos a dar un breve tip&tricks relacionado con el registro y Windows.

  

El otro día publiqué en las redes sociales una [web muy interesante](https://gpsearch.azurewebsites.net/) que vincula una GPO con la rama del registro que le corresponde.

  

En esta ocasión un pequeño truco. ¿Conoces [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer)? La herramienta de Sysinternals para monitorizar procesos del sistema?

  

Podemos ir abriendo servicios y viendo datos del resultado, procesos hijos, el pid, la operación, como siempre. Bien, podemos usar los filtros para indicar dos pequeños filtros.

Uno que el proceso sea MMC.exe, es decir, una consola ( el editor de GPO´s por ejemplo) y otro filtro en el que indicamos que la operación en RegSetValue.

  

[![](https://1.bp.blogspot.com/-qnbCl3WZXV4/XheXJ_ubZZI/AAAAAAAAGfU/qqQNnhhMZisUeDCYYgoYvEMTRoJ2TxSNACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.13.31.png)](https://1.bp.blogspot.com/-qnbCl3WZXV4/XheXJ_ubZZI/AAAAAAAAGfU/qqQNnhhMZisUeDCYYgoYvEMTRoJ2TxSNACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.13.31.png)

  
Una vez que tenemos el filtro, abrimos nuestra editor de GPO´s y modificamos cualquier dato, por ejemplo, la longitud de contraseña... y antes de darle a CLICK para guardar la GPO, volvemos a Process Monitor, aplicamos el filtro, borramos la lista, y hacemos click en la GPO (para guardar).  
  
De esta manera podemos ver con detalle la clave de registro que se ha modificado.  
  
Espero que os sirva de ayuda en alguna ocasión.  
  
Gracias por leerme !!!