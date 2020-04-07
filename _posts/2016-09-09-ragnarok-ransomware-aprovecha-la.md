---
title: 'Ragnarok Ransomware aprovecha la vulnerabilidad de Citrix para apuntar
a servidores vulnerables'
date: 2020-01-30T20:41:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-XCQtRNyAWMU/XjMxH9DxIBI/AAAAAAAALtg/Gj-qX7o6mXcsa9n1_crlBf9cp2IsrHdtQCLcBGAsYHQ/s640/ransomware-100739759-large.3x2-700x445.jpg)](https://1.bp.blogspot.com/-XCQtRNyAWMU/XjMxH9DxIBI/AAAAAAAALtg/Gj-qX7o6mXcsa9n1_crlBf9cp2IsrHdtQCLcBGAsYHQ/s1600/ransomware-100739759-large.3x2-700x445.jpg)

  

Otro incidente para enfatizar la necesidad de parchear la grave vulnerabilidad de Citrix (CVE-2019-19781). Un nuevo ransomware llamado Ragnarok se dirige activamente a los servidores vulnerables de Citrix ADC. 

  

Los investigadores de Citrix han encontrado nuevos ransomware involucrados en atacar servidores vulnerables de Citrix ADC. Como se reveló, los cibercriminales están explotando la infame vulnerabilidad de Citrix (CVE-2019-19781) para atacar máquinas vulnerables. 

  

Los atacantes primero comprometen los dispositivos vulnerables de Citrix ADC. Si tienen éxito, luego descargan scripts para buscar máquinas Windows vulnerables a EternalBlue. Luego, al encontrar dispositivos vulnerables, el script inyecta una DLL para descargar y ejecutar el ransomware Ragnarok. Si bien parece un ransomware típico, también presenta algunas diferencias significativas que lo hacen único. Al principio, excluye a Rusia y China de los ataques de cifrado. Para esto, verifica el ID de idioma de Windows. 

  

A continuación, intenta deshabilitar Windows Defender de Microsoft para evitar cualquier verificación de seguridad. También tiende a deshabilitar la reparación de inicio automática, borra las instantáneas de volumen y cierra el Firewall de Windows. Sin embargo, el proceso de encriptación de Ragnarok es similar a otro ransomware. Es decir, utiliza el cifrado AES para cifrar los archivos, mientras que cifra la clave generada con la clave de cifrado RSA incluida. También cambia el nombre de los archivos cifrados agregando una extensión ".ragnarok". Al escanear los datos, omite cualquier archivo del sistema o aquellos con ".exe", ".dll", ".sys", junto con algunas otras rutas de archivos especificadas. 

  

Se lanzó el parche de vulnerabilidad de Citrix Por ahora, no es posible remediar un ataque de cifrado Ragnarok. En consecuencia, los usuarios deben tener mucho cuidado con su seguridad. Los usuarios de Windows ciertamente pueden evitar este ataque activando la "Protección contra manipulaciones de Microsoft" en Windows 10 que evita los cambios en Windows Defender. Los usuarios deben asegurarse de parchear la vulnerabilidad de Citrix en primer lugar para evitar Ragnarok y otros posibles ataques que exploten la falla. 

  

  
  

Fuente: [https://latesthackingnews.com/](https://latesthackingnews.com/2020/01/30/ragnarok-ransomware-exploits-citrix-vulnerability-to-target-vulnerable-servers/)

No olvides Compartir... 

  

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)