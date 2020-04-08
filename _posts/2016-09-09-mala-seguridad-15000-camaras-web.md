---
title: 'Mala seguridad: 15,000 cámaras web privadas expuestas.'
date: 2019-10-04T07:00:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-6H3J8iTdZVE/XZX61rTqgHI/AAAAAAAALFE/NZePzNMw5EAnp3vTWow0QBa_uVepdk8XwCLcBGAsYHQ/s640/smartphone-1445489_960_720.jpg)](https://1.bp.blogspot.com/-6H3J8iTdZVE/XZX61rTqgHI/AAAAAAAALFE/NZePzNMw5EAnp3vTWow0QBa_uVepdk8XwCLcBGAsYHQ/s1600/smartphone-1445489_960_720.jpg)

  

Cada artículo de seguridad cibernética que encontrará incluirá algún tipo de recordatorio que enfatice el uso de contraseñas seguras, un buen software antivirus y lo habitual. Sin embargo, se tiene menos cuidado para garantizar que los componentes de hardware de nuestras computadoras sean seguros.

  

A raíz de esto, Avishai Efrat, un hacker de sombrero blanco de Wizcase, ha encontrado 15,000 cámaras web en todo el mundo a las que se puede acceder sin autorización, con el único requisito previo de conexión a Internet. Muchas de estas cámaras web también pueden ser manipuladas por usuarios maliciosos que editan su configuración, lo que se hace más fácil por el hecho de que la mayoría de los usuarios no se molestan en cambiar las credenciales predeterminadas de dichos dispositivos.

  

Algunos de los fabricantes incluyen:

  

1\. Cámaras de red AXIS

2\. Cámara web de Cisco Linksys

3\. Servidor de logotipo de cámara IP

4\. Webcam IP

5\. Cámara web IQ Invision Cámara IP Mega-Pixel,

6\. Mobotix

7\. WebCamXP 5

8\. Yawcam.

  

Se han encontrado instalados tanto para uso doméstico como comercial en diferentes países, siendo los siguientes los más populares según lo [informado por Wizcase](https://www.wizcase.com/blog/webcam-security-research/):

  

1\. Argentina

2\. Australia

3\. Austria

4\. Brasil

5\. Canadá

6\. Francia

7\. Alemania

8\. Italia

9\. Japón

10\. Pakistán

11\. Rusia

12\. España

13\. Suiza

14\. Reino Unido

15\. EE.UU.

16\. Vietnam

  

Si bien se esperaría que las cámaras web en los hogares revelaran principalmente información confidencial personal en países en desarrollo donde la tendencia del trabajo remoto es menor, esto no es cierto para las economías basadas particularmente en Europa y las Américas, donde los datos comerciales importantes también pueden haber sido comprometidos.

  

Pero eso no es donde termina. Los usos potenciales de las cámaras web también se extienden a lugares de culto, museos, áreas deportivas y estacionamientos que podrían considerarse como una invasión a la privacidad de los usuarios.

  

Aquí, es digno de mención que desde 2014, un sitio web llamado "Insecam" ha mostrado filmaciones en vivo de más de 100,000 cámaras de seguridad privadas inseguras de todo el mundo. El sitio afirma ser "El directorio más grande del mundo de cámaras de seguridad de vigilancia en línea".

  

Algunas de las consecuencias de esto son que se pueden usar imágenes indecentes de personas para chantajearlas, el robo de propiedad intelectual podría ser más fácil para las empresas poco éticas que pueden utilizar dichos feeds, la vigilancia se vuelve más fácil tanto para las agencias gubernamentales gubernamentales como extranjeras, los bucles de cámara podrían configurarse para coordine ataques físicos y mucho más: la lista es interminable para decir.

  

La pregunta de oro es, ¿por qué varios fabricantes pasaron por alto este defecto a pesar de las implicaciones? Para responder esto, debemos ver cómo funcionan las cámaras web. Cada vez que se instala uno, los usuarios necesitan alguna forma remota para acceder a sus imágenes, ya sea en tiempo real o más tarde para la reproducción. Es importante darse cuenta de esto, ya que no todas las cámaras web se utilizan para la comunicación de redes de video y muchas de ellas se utilizan con fines de seguridad.

  

Los mecanismos de acceso se pueden dividir en dos protocolos de red, a saber, reenvío de puertos y punto a punto (P2p). En el reenvío de puertos mediante el uso de la tecnología Universal Plug and Play (UPnP), se puede acceder a la cámara mediante un puerto en la dirección IP externa.

[![](https://1.bp.blogspot.com/-Pwyi2uLSFgI/XZX7Q6jo8hI/AAAAAAAALFM/uYjzJYre-f4rNFGKtRkfglaYYV_lK7fIACLcBGAsYHQ/s400/Diagram.jpg)](https://1.bp.blogspot.com/-Pwyi2uLSFgI/XZX7Q6jo8hI/AAAAAAAALFM/uYjzJYre-f4rNFGKtRkfglaYYV_lK7fIACLcBGAsYHQ/s1600/Diagram.jpg)

Una ilustración del atacante que explota vulnerabilidades en el proceso de reenvío de puertos, imagen de Wizcase

  

Si no hay un método de autenticación, cualquier persona que conozca la dirección IP del dispositivo puede acceder a las imágenes y a otros privilegios según la configuración del fabricante. En segundo lugar, en P2P, el dispositivo se comunica con los servidores del fabricante para la administración y otras funciones sin reenvío de puertos, sin necesidad de reenvío de puertos.

  

Sin embargo, esto puede volver a ser inseguro si el fabricante no toma las precauciones básicas mencionadas anteriormente. Para resolver estos problemas de seguridad, Chase de Wiscase ofrece información sobre las siguientes líneas:

  

_**"Muchos dispositivos no están protegidos por firewalls, VPN o acceso a la lista blanca de IP, ninguno de los cuales negaría escáneres y conexiones arbitrarias. Si estos dispositivos tienen servicios de red abiertos, podrían estar expuestos. escribió Chase "." La postura de seguridad del dispositivo puede depender de diferentes cosas, pero una forma recomendada de configurar una cámara web segura sería utilizar una red VPN local, de modo que cualquier puerto abierto permanezca dentro de los límites de la comunicación cifrada del VPN La aplicación se conectaría a la VPN, que luego accedería al puerto utilizando una IP interna, evitando así los problemas potenciales de abrir el puerto y llamar a casa y eliminando los puertos accesibles de su IP externa ”**_, concluyó Chase.

  

Además, también se pueden agregar otras medidas, como incluir en la lista blanca solo las direcciones MAC del propio dispositivo, elegir proveedores con un enfoque en la seguridad, habilitar la autenticación de dos factores y finalmente usar una conexión cifrada para acceder al panel de administración.

  

Finalmente, si no es un usuario técnicamente interesado, verificar si su dirección IP pública se ve comprometida a través de un motor de búsqueda como Shodan también puede ayudarlo de inmediato a ayudarlo a decidir su próximo curso de acción.  
  
  

Fuente: [https://www.hackread.com/](https://www.hackread.com/5000-private-webcams-exposed-to-creeps/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)