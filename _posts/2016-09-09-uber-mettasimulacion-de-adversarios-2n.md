---
title: 'Uber Metta...Simulación de adversarios 2/n'
date: 2019-09-30T17:00:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
En otro [artículo de la serie](http://kinomakino.blogspot.com/2019/09/caldera-simulacion-de-adversarios-golpe.html) introducimos el concepto de simulación de adversarios con el software [Caldera](https://kinomakino.blogspot.com/2019/09/caldera-simulacion-de-adversarios-golpe.html). Te refresco, lanzar ataques de manera controlada sobre un sistema para evaluar sus capacidades de detección.  
  

[![](https://1.bp.blogspot.com/-qGssI3GR7zE/XZIndDz-TSI/AAAAAAAAGYI/xREVKzAvDrQFU03NgPSyPyWGsTAS2zTpQCLcBGAsYHQ/s400/hqdefault.jpg)](https://1.bp.blogspot.com/-qGssI3GR7zE/XZIndDz-TSI/AAAAAAAAGYI/xREVKzAvDrQFU03NgPSyPyWGsTAS2zTpQCLcBGAsYHQ/s1600/hqdefault.jpg)

  
Al más puro estilo caldera, con línea de comandos, hoy presentamos [Uber Metta](https://github.com/uber-common/metta).  
  
El sistema [Metta](https://github.com/uber-common/metta) trabaja con [Vagrants](https://albertoromeu.com/guia-rapida-vagrant/), lo que son un conjunto de configuraciones para desplegar imágenes virtualbox con un setting concreto. Lo que podría ser un contenedor basado en VirtualBox.  
  
La parte de instalación de muy sencilla, podemos seguir el [tutorial del autor. ](https://github.com/uber-common/metta/blob/master/setup.md)  

  
Para este prueba, vamos a usar un Vagrant con Windows 10, en [concreto el siguiente](https://github.com/uber-common/metta/wiki/Vagrants) que os acompaño y que usamos para algunas cosas.   
  
Uses el que uses, como indica el autor, habilita la comunicación hacia él mediante WINRM, al menos, para poder operar con las pruebas que trae por defecto Metta.  
  
  
```
https://github.com/uber-common/metta/wiki/Vagrants  
vagrant init StefanScherer/windows\_10  
vagrant up
``````
  

``````
Al final, el autor de la herramienta "evita" la parte de RAT de [Caldera](https://kinomakino.blogspot.com/2019/09/caldera-simulacion-de-adversarios-golpe.html) con el despliegue de una máquina Windows 10 con Sysmon para probar las detecciones. No es lo más elegante ni funcional, ya que tienes tu que acceder al Windows virtualizado para ver a mano los logs, los eventos que han aparecido, pero bueno, demasiado ha hecho y agradecidos estamos !!!
```

  
El placer de las cosas bien hechas aparece:  
  

[![](https://1.bp.blogspot.com/-W_JvrvaPQEY/XYpkdbWAwiI/AAAAAAAAGX8/AaVCZhpORyUBYeaDcHLOs2Cbzd8OI5kGQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-09-24%2Ba%2Blas%2B20.45.34.png)](https://1.bp.blogspot.com/-W_JvrvaPQEY/XYpkdbWAwiI/AAAAAAAAGX8/AaVCZhpORyUBYeaDcHLOs2Cbzd8OI5kGQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-09-24%2Ba%2Blas%2B20.45.34.png)

  
Lo que realmente estamos lanzando son las acciones descritas en el yaml.  
  

enabled: true

meta:

author: cg

created: 2017-06-01

decorations:

\- Purple Team

description: On Target Recon Atack Simulation.

link: https://carnal0wnage.attackresearch.com

mitre\_attack\_phase: Discovery

mitre\_attack\_technique: Account Discovery

purple\_actions:

1: cmd.exe /c net user

2: cmd.exe /c net user /domain

3: cmd.exe /c net localgroup administrators

4: cmd.exe /c net view

5: cmd.exe /c net view /domain

6: cmd.exe /c net groups \\"Domain Admins\\" /domain

7: cmd.exe /c net use

8: cmd.exe /c net share

9: cmd.exe /c ipconfig /all

10: cmd.exe /c tasklist /v

11: cmd.exe /c gpresult /z

12: cmd.exe /c nltest /dclist:corp

os: windows

name: On-target Recon Simulation

uuid: 017df153-470e-43d6-8e91-24c6b7cf62c4

En este caso, muy sencillitas, y tiene algún repositorio con algunas cosas graciosas.  
  
Al final, no deja de ser una manera de ejecutar los comandos, lo que denomina las Purple Actions.  
  
Habrá que ver como evoluciona el proyecto.