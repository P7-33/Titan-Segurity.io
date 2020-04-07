---
title: 'T1034. Enumera y soluciona el problema de las comillas en servicios de
Windows !!!'
date: 2020-01-16T20:25:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
En el episodio de hoy vamos a comentar una pequeña herramienta o truco para ayudarnos a fortificar y/o atacar nuestros sistemas Windows, como siempre, depende del rol que te toque.  
  
Siguiendo el Framework MITRE, vamos a hablar de la técnica [T1034](https://attack.mitre.org/techniques/T1034/), en concreto Path Interception. Empleada como mecanismo de persistencia, aprovecha una vulnerabilidad de concepto en los servicios Windows para ejecutar de manera controlada binarios.  
  
El concepto es sencillo. En los sistemas Windows arrancamos servicios, y si en los nombres del ejecutable del servicio hay espacio y no se ha empleado las comillas, por ejemplo "c:\\mi compañia\\mi programa\\programa.exe" el comportamiento es que el sistema intentará buscar programa.exe de la siguiente manera:  
  
  

C:\\archivos de programa\*\\empresa\*\\nombredeprograma\*\\programa.exe\*

C:\\programa.exe

C:\\archivos de programa\\programa.exe

C:\\archivos de programa\\empresa\\programa.exe

C:\\archivos de programa\\empresa\\nombredeprograma\\programa.exe

  
  
Buscará primero el binario en cada uno de los sitios que he puesto asterisco.  
  
Si conocemos esto, y podemos escribir en cualquier de esas ubicaciones, podemos colocar nuestra pieza de software, nuestro malware/stager/etc... y que se ejecute cada vez que se inicie el servicio (por ejemplo, cada vez que se inicie el sistema).  
  
El concepto de Services Hijacking es muy viejo, pero el comentarlo es porque aún veo muchos entornos en los que esto no se cuida.  
  
Lo interesante de esto es que podemos usar alguna de las herramientas que hay para enumerar, pero [en este que os traigo](https://gallery.technet.microsoft.com/scriptcenter/Windows-Unquoted-Service-190f0341), tenemos la posibilidad de no solo listar los servicios del Windows que tienen un ejecutable con espacios en los nombres y no tiene comillas !!!! y si queremos, nos modifica el servicio para incluir las comillas, es decir, para solucionarlo.  
  

[![](https://gallery.technet.microsoft.com/scriptcenter/site/view/file/136819/1/before_service_fix.png)](https://gallery.technet.microsoft.com/scriptcenter/site/view/file/136819/1/before_service_fix.png)

  

[![](https://gallery.technet.microsoft.com/scriptcenter/site/view/file/136820/1/after_service_fix.png)](https://gallery.technet.microsoft.com/scriptcenter/site/view/file/136820/1/after_service_fix.png)

  
Como ves en las imágenes de la propia herramienta, el concepto es muy sencillo.  
  
Espero que te sirva de ayuda tanto si vas a atacar, como si vas a proteger.  
  
También, podríamos usar este dato en el SIEM, si trazamos la actividad con SYSMON, preguntando algo así como: si el papa es service.exe y el proceso no es: '\\''.\*' y algunas cosita más, podrás descubrirlos "in the wild" sin tener que ir al equipo a pasarle la tool...  
  
Bueno, como siempre, dale el uso que quieras, gracias por leerme !!!