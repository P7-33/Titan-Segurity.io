---
title: 'Ryuk Ransomware deja de cifrar carpetas de Linux'
date: 2019-12-27T16:45:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-8Bsm0IewiRI/XgYnFCysiFI/AAAAAAAALiU/ZybPSzN3QUc5whJLye8QWK978EzcnMtBACLcBGAsYHQ/s640/Ryuk.png)](https://1.bp.blogspot.com/-8Bsm0IewiRI/XgYnFCysiFI/AAAAAAAALiU/ZybPSzN3QUc5whJLye8QWK978EzcnMtBACLcBGAsYHQ/s1600/Ryuk.png)

  

Se lanzó una nueva versión del Ryuk Ransomware que evitará encriptar carpetas que se ven comúnmente en los sistemas operativos \* NIX.

  

Después de que la ciudad de Nueva Orleans fue infectada por el ransomware, [BleepingComputer confirmó](https://www.bleepingcomputer.com/news/security/ryuk-ransomware-likely-behind-new-orleans-cyberattack/) que la ciudad fue infectada por el Ryuk Ransomware utilizando un ejecutable llamado v2.exe.

  

Después de analizar la muestra [v2.exe](https://www.virustotal.com/gui/file/1b424c3edf0b2e241050345432731cd804b1e273fc3c470d660c66393891cccc/detection), el investigador de seguridad Vitali Kremez compartió con BleepingComputer un [cambio interesante](https://twitter.com/VK_Intel/status/1208577165652049920?s=20) en el ransomware; ya no cifraría las carpetas asociadas con los sistemas operativos \* NIX.

  

[![](https://1.bp.blogspot.com/-I7xEkj6WbQ8/XgYl4QSFWEI/AAAAAAAALiM/4I6dAWIHJYEJsk0iqN8Qy-kFHLfytAY4ACLcBGAsYHQ/s640/1.jpg)](https://1.bp.blogspot.com/-I7xEkj6WbQ8/XgYl4QSFWEI/AAAAAAAALiM/4I6dAWIHJYEJsk0iqN8Qy-kFHLfytAY4ACLcBGAsYHQ/s1600/1.jpg)

  

  
  

Blacklist \*NIX Folders

La lista de carpetas de Ryuk \* NIX en la lista negra:

```


  
bin

  
`

  
boot

  
Boot  

  
etc

  
dev  
lib  

  
sbin

  
initrd  
sys  

  
var

  
vmlinuz  

  
run

  
`
```

A primera vista, parece extraño que un malware de Windows ponga en la lista negra \* carpetas NIX al cifrar archivos.

Aún más extraño, Kremez nos dijo que le habían preguntado en numerosas ocasiones si había una variante Unix de Ryuk, ya que los datos almacenados en estos sistemas operativos se han cifrado en los ataques de Ryuk.

No existe una variante de Linux / Unix de Ryuk, pero Windows 10 contiene una característica llamada Subsistema de Windows para Linux (WSL) que le permite instalar varias distribuciones de Linux directamente en Windows. Estas instalaciones utilizan carpetas con los mismos nombres en la lista negra que se enumeran anteriormente.

Con la creciente popularidad de WSL, los actores de Ryuk probablemente cifraron una máquina Windows en algún momento que también afectó a las carpetas del sistema \* NIX utilizadas por WSL. Esto habría causado que estas instalaciones WSL ya no funcionen.

"Definitivamente tienen casos que afectan los entornos WSL, lo que probablemente los llevó a poner en la lista negra las carpetas NIX como lo hacen de manera similar con las de Windows. Es nuevo para mí y podría explicar por qué Ryuk y cómo Ryuk afecta las máquinas NIX a través de WSL", dijo Kremez a BleepingComputer.

Como el objetivo del ransomware más exitoso es encriptar los datos de una víctima, pero no afectar la funcionalidad del sistema operativo, este cambio tiene sentido.

Con estas carpetas en la lista negra, Ryuk elimina un dolor de cabeza adicional con el que tendrían que lidiar para un cliente que paga cuyas instalaciones de WSL están arruinadas.  
  
  

Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/ryuk-ransomware-stops-encrypting-linux-folders/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)