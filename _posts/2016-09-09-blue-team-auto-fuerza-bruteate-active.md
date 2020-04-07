---
title: 'Blue Team: auto-fuerza-bruteate !!! Active Directory'
date: 2020-01-05T16:04:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
En el post de hoy vamos a hablar de un concepto y herramienta defensiva relacionado con la fuerza bruta. Me refiero a realizar estas pruebas contra el directorio activo que gestionamos.  
  
Imagina que quieres lanzar un proceso de fuerza bruta contra TODO tu AD. No existe, o no conozco, una manera de hacerlo sin que intervengan las GPO´s de bloquee de cuentas por ejemplo. Es decir, que si lanzas el ataque de fuerza bruta por ejemplo desde una IP, el AD no te bloquee el usuario destino... Si existe estaría bien saberlo.  
  
Con una política de seguridad de contraseñas compleja, como las que conocemos, no es suficiente, o no debería serlo, para proteger la identidad de nuestros preciados usuarios de AD. Por ejemplo, una clave de 10 caracteres, alfanuméricos, que se cambie, el historial, balbalbal, está mejor que usar 12345, pero en la realidad, esta clave tampoco es segura: nombre\_empresa2020!"# o similares.  
  
Si a esto le sumas el constante chorreo de leaks de contraseñas que aparecen de ataques a terceros, tenemos una abanico de posibilidades de que un usuario esté usando una contraseña SEGURA para Active Directory pero no para un atacante.  
  

[![](https://1.bp.blogspot.com/-epob2ZWh8HU/XhH6Wp5VM6I/AAAAAAAAGeI/I9XJTJlPosgAukq-R1NZJp4jmPBe4m6vQCLcBGAsYHQ/s400/Brute_Force-327040569-large.jpg)](https://1.bp.blogspot.com/-epob2ZWh8HU/XhH6Wp5VM6I/AAAAAAAAGeI/I9XJTJlPosgAukq-R1NZJp4jmPBe4m6vQCLcBGAsYHQ/s1600/Brute_Force-327040569-large.jpg)

  
Para esto podemos hacer varias gestiones, pero podemos aprovecharnos de la capacidad que tiene DSinternals por ejemplo para de manera controlada, autenticada... puedes exportar el contenido de tu NTDIS... de tu base de datos de usuarios del directorio, en formato NTLM. [En este artículo lo vimos.](http://kinomakino.blogspot.com/2016/10/dsinternals-adquirir-el-listado.html)  
  
Ahora vamos a usar la herramienta [bAd-Passwords](https://github.com/ZilentJack/Get-bADpasswords) del señor [https://twitter.com/JakobHeidelberg](https://twitter.com/JakobHeidelberg) que lo que hace es exactamente lo que queremos. Lee el directorio activo, pasa a NTLM una o varias listas de contraseñas y las compara.  
  
El trabajo previo de generar una lista de contraseñas lo podemos hacer con varias herramientas, en el [próximo post](https://kinomakino.blogspot.com/2020/01/una-de-wordlist-mentalist.html) os paso una y una lista, o usar los diccionarios de filtraciones que hay...  
  

[![](https://1.bp.blogspot.com/-Yp4Ctf4CRFY/XhH5kAUW6QI/AAAAAAAAGeA/7atAE5FgK_U-YPqO6Ij8WPL5aGwKItiggCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-05%2Ba%2Blas%2B15.53.42.png)](https://1.bp.blogspot.com/-Yp4Ctf4CRFY/XhH5kAUW6QI/AAAAAAAAGeA/7atAE5FgK_U-YPqO6Ij8WPL5aGwKItiggCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-05%2Ba%2Blas%2B15.53.42.png)

  
De esta manera podemos auditar periódicamente si alguno de nuestros usuarios está usando una contraseña que cumple con los criterios de la política, pero que para un mega-hacker rico de la muerte podría ser fácil de adivinar.  
  
Como siempre, espero que os guste.  
  
Gracias por leerme !!!