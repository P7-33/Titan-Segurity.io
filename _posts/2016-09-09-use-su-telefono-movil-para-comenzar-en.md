---
title: 'Use su teléfono móvil para comenzar en pentesting básico'
date: 2020-02-09T18:15:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-iVo8uJGyk2I/XkA-cRDZFDI/AAAAAAAALws/cqPNLl-Co70Wzz7omrXWVdpmM8ILX3pyQCLcBGAsYHQ/s640/business-2056029_960_720.jpg)](https://1.bp.blogspot.com/-iVo8uJGyk2I/XkA-cRDZFDI/AAAAAAAALws/cqPNLl-Co70Wzz7omrXWVdpmM8ILX3pyQCLcBGAsYHQ/s1600/business-2056029_960_720.jpg)

  
Android es el sistema operativo más popular en dispositivos móviles y ofrece múltiples opciones para maximizar la experiencia del usuario. Acorde a especialistas en **[hacking ético](https://www.iicybersecurity.com/curso-hacking.html)**, muchos cambios en los dispositivos pueden realizarse después de rootear el dispositivo, aunque un smartphone con Android sin rootear también es realmente funcional. A continuación le mostraremos una aplicación de Android que funciona como un software de **[pentesting](https://noticiasseguridad.com/tutoriales/herramientas-para-pentesting-y-programas-de-recompensas-de-vulnerabilidades/)** básico. 

  

Empleando este software es posible realizar algunas tareas de escaneo de red básico como: verificar la dirección IP de destino de la aplicación web, rastrear el enrutamiento de cualquier sitio web, consulta Whois, dnslookup, netcat y muchas otras características propias del pentesting. Acorde a los expertos en hacking ético del Instituto Internacional de Seguridad Cibernética (IICS) Network Manager puede ser muy útil para comenzar en pentesting.

*   Para las pruebas usaremos un **[Xiaomi](https://noticiasseguridad.com/vulnerabilidades/smartphones-pixel-huawei-xiaomi-oppo-motorola-y-samsung-son-facilmente-hackeables-actualice-lo-antes-posible-aqui-la-lista-completa/)** Redmi Note 4 – Android 7.0 Nougat
*   Descargue la aplicación en: https://play.google.com/store/apps/details?id=com.eakteam.networkmanager&hl=en
*   Esta aplicación también tiene una versión de paga, pero la versión libre también es muy útil
*   Simplemente descargue e instale Network Manager
*   Luego haga clic en el ícono de Network Manager

  
  
  

![Home Screen](https://www.securitynewspaper.com/snews-up/2020/01/n_w-manager-apk-1-576x1024.jpg)

**_Pantalla de inicio_**

*   Network Manager muestra detalles básicos de IP

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/n_w_manager_apk-658x1024.jpg)

**_APK de Network Manager_**

*   Network Manager ofrece muchas funciones para diagnosticar cualquier red local

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/n_w-manager-apk-features-182x1024.jpg)

Funciones de Network Manager

*   Comenzando con Universal Scanner. Este escáner ofrece opciones como búsqueda de IP, búsqueda de DNS, analizador SSL/TLS, escáner de puertos, Whois, Traceroute

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/universal-scanner-1024x460.jpg)

**_Network Manager – Universal Scanner_**

*   Hemos escaneado hack.me para mostrar cómo funciona el administrador de red. Para recopilar información básica de cualquier sitio web, puede usar Universal Scanner
*   Dicha información se puede utilizar en la fase de recopilación de información de pentesting
*   Recopilar detalles con whois

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/whois-hack.me_-267x1024.jpg)

**_Detalles de Whois_**

*   Whois es el primer paso para conocer cualquier información sobre cualquier URL. Proporciona información sobre los detalles de registro del sitio web, el dominio de hosting, etc
*   Network Manager ofrece una opción para conectarse mediante SSH
*   Para las pruebas nos hemos conectado con el sistema Linux. Para la conexión, ingrese el nombre de usuario y la contraseña

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/ssh-connect-576x1024.jpg)

**_Conexión SSH_**

*   Haga clic en conectar, posteriormente se iniciará la sesión del terminal

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/ssh-connection-established-281x500.jpg)

**_Conexión SSH_**

*   SSH se puede utilizar para acceder a cualquier servidor desde cualquier ubicación
*   Comprobación de la velocidad con el administrador de red

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/speedtest-576x1024.jpg)

**_Verificar velocidad de red_**

*   Puede ser útil verificar la velocidad antes de usar Network Manager para recopilar información
*   Uso de Web Crawler en el administrador de red. Esto rastreará mucha información hasta que se detenga

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/web-crawler-695x221.jpg)

**_Web Crawler_**

*   Rastreador web que se requiere para encontrar errores en cualquier sitio web. El rastreador de sitios web muestra todos los enlaces externos, internos e incluso muestra las imágenes, archivos y scripts que se encuentran en el rastreo de sitios web
*   Encuentra el caché de arp. Esto ayuda a saber cuántos usuarios están conectados en la red

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/ARP-cache-1-300x298.jpg)

**_ARP\_Cache_**

*   Arriba se muestran los usuarios conectados con sus direcciones MAC. El atacante puede recopilar direcciones MAC de la red y puede usarse en ataques de envenenamiento por ARP
*   Verifique la URL antes de abrirla en el navegador

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/url-checker-811x1024.jpg)

**_Verificación de URL segura_**

*   Arriba se muestra que hackthissite.org es seguro para visitar. Para verificar cualquier URL sospechosa, los usuarios pueden usar la comprobación de URL de navegación segura
*   Análisis de SSL: verificar si la URL está protegida con SSL o no

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/SSL_Analyzer-335x500.jpg)

**_Análisis de SSL_**

*   Arriba se muestra la versión del certificado SSL con SSL Cipher
*   Otra opción es el escáner de puertos, que muestra los puertos abiertos de la URL de destino. Certifiedhacker.com se utiliza para realizar pruebas, mencionan los expertos en hacking ético

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/portscanner-281x500.jpg)

**_Escaneo de puertos_**

*   Arriba se muestran los puertos abiertos de certifiedhacker.com. Cuantos más puertos estén abiertos, más sitio web puede ser vulnerable
*   La calculadora de IP también se puede utilizar para proporcionar información sobre cuántos usuarios puede manejar una red

  
  
  

![](https://www.securitynewspaper.com/snews-up/2020/01/IP-calculator-346x550.jpg)

**_Cálculo de IP_**

*   La captura de pantalla anterior hace referencia a 254 direcciones disponibles, mencionan los especialistas en hacking ético

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/tutoriales/use-su-telefono-movil-para-comenzar-en-pentesting-basico/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)