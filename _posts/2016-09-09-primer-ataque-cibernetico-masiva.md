---
title: 'Primer ataque cibernético ''Explotación masiva'' mediante la falla
BlueKeep RDP'
date: 2019-11-05T03:53:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-uQlwt9UIB8M/XcDhY-XFsfI/AAAAAAAALOY/ha5_N1RBMLsdlyM9MgSdU0WC6Rza_UbKwCLcBGAsYHQ/s640/bluekeep-wormable-rdp-cyberattack.png)](https://1.bp.blogspot.com/-uQlwt9UIB8M/XcDhY-XFsfI/AAAAAAAALOY/ha5_N1RBMLsdlyM9MgSdU0WC6Rza_UbKwCLcBGAsYHQ/s1600/bluekeep-wormable-rdp-cyberattack.png)

  

Investigadores de ciberseguridad han descubierto un nuevo ataque cibernético que se cree que es el primer intento de la infame vulnerabilidad BlueKeep RDP para comprometer en masa los sistemas vulnerables para la minería de criptomonedas.  
  
En mayo de este año, Microsoft lanzó un parche para un error de ejecución de código remoto altamente crítico, denominado BlueKeep, en sus Servicios de escritorio remoto de Windows que podría explotarse de forma remota para tomar el control total de los sistemas vulnerables simplemente enviando solicitudes especialmente diseñadas sobre RDP.  
  
BlueKeep, rastreado como CVE-2019-0708, es una vulnerabilidad que se puede eliminar porque puede ser armado por un posible malware para propagarse automáticamente de una computadora vulnerable a otra sin requerir la interacción de las víctimas.  
  
Se ha considerado que BlueKeep es una amenaza tan grave que desde su descubrimiento, Microsoft e incluso las agencias gubernamentales \[NSA y GCHQ\] han estado alentando continuamente a los usuarios y administradores de Windows a aplicar parches de seguridad antes de que los piratas informáticos se apoderen de sus sistemas.  
  
Incluso muchas firmas de seguridad e investigadores individuales de ciberseguridad que desarrollaron con éxito un exploit totalmente funcional para BlueKeep se comprometieron a no lanzarlo al público por un bien mayor, especialmente porque casi un millón de sistemas se encontraron vulnerables incluso un mes después del lanzamiento de los parches.  
  
Esta es la razón por la cual los piratas informáticos aficionados tardaron casi seis meses en encontrar un exploit BlueKeep que todavía no es confiable y ni siquiera tiene un componente que se pueda eliminar.  
  
**BlueKeep Exploit extiende malware de criptomonedas**  
  
La explotación de BlueKeep fue especulada por primera vez por Kevin Beaumont un sábado cuando sus múltiples sistemas de honeypot EternalPot RDP se bloquearon y se reiniciaron repentinamente.  
  
**Vulnerabilidad de rdp wormable bluekeep**  
  
Marcus Hutchins, el investigador que ayudó a detener el brote de ransomware WannaCry en 2017, luego analizó los volcados de memoria compartidos por Beaumont y confirmó "artefactos BlueKeep en la memoria y el código de shell para lanzar un Monero Miner".  
  
    En una publicación de blog publicada hoy, Hutchins dijo: "Finalmente, confirmamos que este segmento \[en un volcado de memoria\] apunta a un shellcode ejecutable. En este punto, podemos afirmar intentos válidos de explotación de BlueKeep en la naturaleza, con un shellcode que incluso coincide con el del shellcode en el módulo BlueKeep Metasploit! "  
  
  
El exploit contiene comandos codificados de PowerShell como carga útil inicial, que luego descarga el binario ejecutable malicioso final de un servidor remoto controlado por el atacante y lo ejecuta en los sistemas de destino.  
  
Según el servicio de escaneo de malware VirusTotal de Google, el binario malicioso es un malware de criptomonedas que extrae Monero (XMR) utilizando la potencia informática de los sistemas infectados para generar ingresos para los atacantes.  
  
**¡Pero no es un ataque Wormable!**  
  
Hutchins también confirmó que el malware propagado por este exploit de BlueKeep no contiene ninguna capacidad de propagación automática para saltar sin ayuda de una computadora a otra.  
  
En cambio, parece que los atacantes desconocidos primero escanean Internet para encontrar sistemas vulnerables y luego los explotan.  
  
En otras palabras, sin un componente susceptible de gusano, los atacantes solo podrían comprometer los sistemas vulnerables que están directamente conectados a Internet, pero no aquellos que están conectados internamente y son accesibles desde ellos.  
  
Aunque los piratas informáticos sofisticados ya podrían haber estado explotando la falla BlueKeep para comprometer sigilosamente a las víctimas específicas, afortunadamente, la falla aún no se ha explotado a mayor escala, como los ataques de WannaCry o NotPetya, como se especuló inicialmente.  
  
Sin embargo, al momento de escribir este artículo, no está claro cuántos sistemas BlueKeep vulnerables de Windows se han visto comprometidos en los últimos ataques cibernéticos para implementar el minero Monero en la naturaleza.  
  
¿Para protegerte? Permítame intentarlo de nuevo: vaya y solucione la maldita vulnerabilidad si usted o su organización todavía está utilizando los sistemas vulnerables de Windows BlueKeep.  
  
Si no es posible solucionar la vulnerabilidad en su organización en cualquier momento antes, puede tomar estas mitigaciones:

*   Deshabilite los servicios RDP, si no es necesario.
*   Bloquee el puerto 3389 utilizando un firewall o hágalo accesible solo a través de una VPN privada.
*   Habilitar la autenticación de nivel de red (NLA): esta es una mitigación parcial para evitar que cualquier atacante no autenticado explote esta falla Wormable.

Fuente: [https://thehackernews.com/](https://thehackernews.com/2019/11/bluekeep-rdp-vulnerability.html)

No olvides Compartir...

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)