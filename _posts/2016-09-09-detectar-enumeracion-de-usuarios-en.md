---
title: 'Detectar enumeración de usuarios en Active Directory mediante
honeytoken: Anti BloodHound, Empire, etc'
date: 2020-01-14T20:11:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
En este artículo vamos a comentar algunas cositas de Blue Team o fortificación de sistemas Windows mediante honeypots.  
  
En este blog hemos hablado mucho de [honeypots](http://kinomakino.blogspot.com/search/label/Honeypot) de todo tipo, [he dado charlas que podéis ver en video](https://www.youtube.com/watch?v=WqOzF0YLDGA), en fin, que me gusta...  
  
Bien, vamos al concepto. Hay muchas herramientas hoy en día que se usan para explotar fallos en el Directorio Activo. De las más conocidas está Empire y su módulo para [reconocer usuarios](https://github.com/EmpireProject/Empire/blob/master/data/module_source/situational_awareness/host/Invoke-WinEnum.ps1) o como pueda ser el [ingestor](https://github.com/BloodHoundAD/BloodHound/tree/master/Ingestors) de [BloodHoud](https://github.com/BloodHoundAD/BloodHound).  
  

[![](https://1.bp.blogspot.com/-HDxGcONWjNw/XheY-TDhJNI/AAAAAAAAGfg/KOzEnQZgTrwHZha3N6IyWIH9ZQ2KTf3GQCLcBGAsYHQ/s640/maxresdefault.jpg)](https://1.bp.blogspot.com/-HDxGcONWjNw/XheY-TDhJNI/AAAAAAAAGfg/KOzEnQZgTrwHZha3N6IyWIH9ZQ2KTf3GQCLcBGAsYHQ/s1600/maxresdefault.jpg)

  
La idea es crearnos un usuarios "honeypot" en el directorio para que, si algún proceso accede a él, nos salte una alarma en la que nos haga sospechar e investigar quien está realizando esa operación de enumeración, que da como resultado un usuario.  
  
Os pongo otro ejemplo en el mundo web por si sirve de concepto. Imagina una web como esta www.miempresa.com en la que no existe www.miempresa.com/rrhh/nominas.  Si por cualquier motivo detecto una petición a ese recurso, es alguien que está buscando por mi web ese directorio... es decir, está enumerando.  El concepto es el mismo pero llevado a Active Directory.  
  
Para ello vamos a hacer lo mismo que hicimos el otro día para [auditar los cambios del registro](http://kinomakino.blogspot.com/2020/01/auditar-cambios-en-el-registro-sin.html), pero está vez lo vamos a hacer sobre un usuario, el comodín.  
  
Creamos un usuario con un nombre cantoso, que no usamos, por ejemplo uso cebo, de "gancho" y de mi pasión por el jamón illooooooo. Ahora accedemos a las opciones avanzadas de seguridad y configuramos la auditoría de acceso sobre este objeto, al final, es un objeto de Active Directory.  
  
Con esto estamos creando un honeyUser, un usuario que si alguien pregunta por él, es porque está haciendo un trabajo masivo de enumeración...  
  

[![](https://1.bp.blogspot.com/-AbcVUdRud6E/Xh4AKxI_99I/AAAAAAAAGf0/I6GzJYhVZfobgLUBjjhuk3RUMDDHnPtNQCLcBGAsYHQ/s640/cebo.png)](https://1.bp.blogspot.com/-AbcVUdRud6E/Xh4AKxI_99I/AAAAAAAAGf0/I6GzJYhVZfobgLUBjjhuk3RUMDDHnPtNQCLcBGAsYHQ/s1600/cebo.png)

[![](https://1.bp.blogspot.com/-eAjL975ACm4/Xh4BfCYVD_I/AAAAAAAAGgA/4n0TohZV-RIJHlAiPuc9lzVzqOBuZX0nQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-14%2Ba%2Blas%2B18.56.04.png)](https://1.bp.blogspot.com/-eAjL975ACm4/Xh4BfCYVD_I/AAAAAAAAGgA/4n0TohZV-RIJHlAiPuc9lzVzqOBuZX0nQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-14%2Ba%2Blas%2B18.56.04.png)

Si todo ha ido bien, cualquier acceso a este fichero daría un evento...

  

Pero ojo, qué pasa cuando entras a usuarios y equipos de Active Directory o usas cualquier comando powershell? Get-ADUser -filter \*

  

p.p1 {margin: 5.0px 0.0px 5.0px 0.0px; font: 10.0px Helvetica}

Aquí tendrías un falso positivo como una casa...

  

El trabajo del analista de eventos es recibir esta alerta, y tratar de discernir si es un usuario administrador haciendo trabajo de administrador, o es una herramienta intentando ejecutar su acometido.

  

Espero que te sirva de ayuda, ya no tanto para estas herramientas, sino en general como idea de las capacidades de detección mediante auditorías.

  

Si quieres aprender a detectar Empire por ejemplo podrás mirar en la monitorización de procesos, buscar codificación de Powershell, consultas de red y muchas más cosas, esto es solo una idea para cualquier enumeración.

  

Para la detección en entorno local forense me gusta este post. [https://holdmybeersecurity.com/2019/02/27/sysinternals-for-windows-incident-response/](https://holdmybeersecurity.com/2019/02/27/sysinternals-for-windows-incident-response/)

  

y para monitorización remota me gusta este: [https://www.swelcher.com/blog/2018/3/29/detecting-powershell-empire](https://www.swelcher.com/blog/2018/3/29/detecting-powershell-empire)

  

Gracias por leerme !!!

p.p1 {margin: 5.0px 0.0px 5.0px 0.0px; font: 10.0px Helvetica}