---
title: 'Guía sobre cómo configurar tu router para optimizar la seguridad de tu
red Wi‑Fi'
date: 2019-12-20T14:31:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-bZvgnTh-R4M/XfzNI4fwtLI/AAAAAAAALgc/KEa6YceZldgdEwOrjTrzWl1esf4nINpIACLcBGAsYHQ/s640/wlan-3131127_960_720.png)](https://1.bp.blogspot.com/-bZvgnTh-R4M/XfzNI4fwtLI/AAAAAAAALgc/KEa6YceZldgdEwOrjTrzWl1esf4nINpIACLcBGAsYHQ/s1600/wlan-3131127_960_720.png)

  

  

Generalmente los routers hogareños cuentan con funcionalidades que, al ser configuradas correctamente, incrementan considerablemente la seguridad de nuestra red. En este post nos centraremos en explicar algunas de ellas.

Al querer mejorar la seguridad de nuestra red es imprescindible tener en cuenta uno de los principios fundamentales de la seguridad informática: la defensa en profundidad. Este principio se basa en la idea de implementar múltiples medidas de seguridad simultáneamente, aunque estas no sean de gran ayuda individualmente. Con esto se busca que un eventual atacante deba evitar múltiples obstáculos, incrementando la probabilidad de que uno de ellos logre detenerlo, o de que advirtamos su presencia antes de que logre su objetivo malicioso. Siguiendo esta idea, buscaremos sacar el mayor provecho a las herramientas ofrecidas por nuestro router con el objetivo de utilizar la mayor cantidad posible de ellas simultáneamente.

Es importante tener presente que no todos los routers cuentan con las mismas funcionalidades y, según la marca y modelo, podría variar el nombre de las mismas y la sección en la que podemos encontrarlas. A su vez, es posible que aquellos modem-routers provistos por los proveedores de servicios de Internet (ISP, por sus siglas en inglés) cuenten con capacidades de configuración muy limitadas. En estos casos, es una muy buena práctica de seguridad utilizar nuestro propio router por detrás del modem-router que nos provee nuestro ISP, ya que es la única manera de tener control total sobre nuestra red, garantizando que ningún operador externo pueda configurarla remotamente.

Por lo tanto, este artículo está enfocado en las posibles configuraciones de manera general; es decir, sin mencionar una marca o modelo concreto, de forma que cualquiera pueda buscarlas e intentar reproducirlas en la página de configuración de su propio router.

#### Cómo obtener la dirección IP de mi router

El primer paso para comenzar con esta tarea será acceder a la configuración de nuestro router. Esto se logra ingresando a la dirección IP del router en un navegador web. Para obtener esta IP basta con realizar los siguientes pasos:

1\. Ingresar a cmd en Windows / terminal en Linux.

2\. Escribir “ipconfig” en Windows / “ip r” en Linux.

3\. Buscar el “default Gateway” de nuestro adaptador de red.

4\. Copiar la IP e ingresarla en el navegador web.

5\. Ingresar el usuario y contraseña por defecto (o el propio en caso de haberlos modificado previamente). Estos pueden ser encontrados buscando el modelo del router en el sitio web del fabricante. Este paso puede no ser necesario en algunos modelos.

  

[![](https://www.welivesecurity.com/wp-content/uploads/2019/12/cmd-1.jpg)](https://www.welivesecurity.com/wp-content/uploads/2019/12/cmd-1.jpg)

Paso 1: En el caso de Windows, ingresamos cmd en el buscador para abrir command prompt.

[![](https://www.welivesecurity.com/wp-content/uploads/2019/12/cmd-2.jpg)](https://www.welivesecurity.com/wp-content/uploads/2019/12/cmd-2.jpg)

Paso 2: escribimos ipconfig, presionamos enter y nos aparecerá la dirección IP para ingresar al sitio de configuración de nuestro router.

También es muy probable que el fabricante haya incluido instrucciones equivalentes en el manual del dispositivo.

Una vez que se ingresó a la página de configuración, se puede comenzar a realizar los siguientes cambios:

#### Modificar usuario y contraseña por defecto para la página de configuración

Los routers suelen estar configurados de fábrica con usuario y contraseña por defecto con el fin de que los usuarios ingresen a la página de configuración y los cambien por los propios. Si no realizamos esta modificación, cualquier atacante que logre ingresar a nuestra red podría acceder a las configuraciones del router simplemente buscando las contraseñas por defecto en el sitio web del fabricante del router, por lo que este paso es fundamental para la seguridad de nuestra red.

#### Utilizar contraseñas complejas en la interfaz de configuración del router

Tanto para el caso del sitio de acceso a la configuración del router como para acceder a las redes Wi-Fi en sí, siempre es conveniente [utilizar contraseñas complejas](https://www.welivesecurity.com/la-es/2016/05/06/crear-contrasena-fuerte-un-minuto/), de al menos 14 caracteres alfanuméricos que incluyan mayúsculas y símbolos, y que no estén relacionadas a nuestro nombre, profesión, domicilio, edad, cumpleaños, mascota, etc. Es decir, seguir las buenas prácticas de elección de contraseñas.

#### Control de acceso a la red: filtrado de dispositivos a través de MAC address

Esta práctica consiste en filtrar que dispositivos podrán conectarse a nuestra red, aun si los mismos cuentan con una conexión física o con la contraseña correcta en el caso de conexión vía Wi-Fi. Esta restricción suele aplicarse sobre [direcciones MAC](https://es.wikipedia.org/wiki/Direcci%C3%B3n_MAC) y hay dos formas de implementarla:

*   Blacklist: todos los dispositivos que se incluyan en esta lista no podrán acceder a la red.
*   Whitelist: todos los dispositivos que se incluyan en esta lista podrán acceder a la red.

Como regla general, en las aplicaciones de seguridad suele convenir filtrar mediante whitelist. Esto tiene sentido, ya que uno conoce todos los dispositivos que posee, pero no conoce todos los dispositivos que no posee. Luego, el objetivo de esta regla es restringir el acceso a la red, permitiéndolo únicamente a los dispositivos que conocemos y que sabemos son confiables. Esto es muy útil en el caso de que un atacante consiguiera la contraseña de nuestra red Wi-Fi y quisiera ingresar para continuar su ataque internamente.

#### Desactivar la opción de administración remota del router

Esta configuración permite que un dispositivo que se encuentra dentro de la red pueda acceder a la página web de configuración del router a través del Wi-Fi. Si bien no siempre es posible, se recomienda que esta configuración esté desactivada, logrando así que solo aquellos dispositivos que están conectados al router físicamente mediante un cable puedan configurarlo. El objetivo de esto es que, si un atacante lograra vulnerar la seguridad de nuestra red Wi-Fi, no podría acceder a dichas configuraciones a menos que comprometa a un equipo que sí pertenezca a la red cableada.

Algunos routers cuentan con la posibilidad de filtrar aún más este acceso especificando exactamente cuales dispositivos cableados pueden acceder, lo cual añadiría aún más seguridad. Esta configuración suele realizarse mediante una whitelist con las direcciones MAC de los dispositivos permitidos.

#### Protocolo de seguridad de la red Wi-Fi

En caso de querer proteger nuestra red Wi-Fi con una contraseña, tanto para prevenir intrusos como para maximizar nuestra seguridad y privacidad, será necesario elegir el protocolo de seguridad a utilizar. Las opciones que suelen estar disponibles en los routers hogareños son tres: WEP, WPA y WPA2. Actualmente la utilización de WEP y WPA esta desaconsejada, ya que estos protocolos no son tan seguros como WPA2 e incluso existen múltiples ataques contra ellos. En caso de no contar con la opción de WPA2, la opción de WPA sería la segunda mejor, ya que WEP es muy inseguro.

Una vez que elegimos WPA2 podemos encontrarnos con dos opciones: personal y Enterprise. Para uso hogareño es aconsejable la versión personal, ya la que la [versión Enterprise requiere tener instalado un servidor Radius](https://www.welivesecurity.com/la-es/2015/03/18/peligro-mala-gestion-wi-fi-empresas/) para manejar las contraseñas.

Una vez que elegimos WPA2 personal es posible que nos encontremos con otras dos opciones relacionadas a qué algoritmo de cifrado utilizará nuestra red: AES o TKIP. Dado que TKIP es un algoritmo más antiguo y considerado menos seguro, se aconseja utilizar AES.

#### Aislar dispositivos conectados vía Wi-Fi

Muchos routers cuentan con la funcionalidad de aislar a los dispositivos que se conectan a la red Wi-Fi de forma que estos no puedan comunicarse entre ellos, pero que sí puedan conectarse a Internet. Se recomienda activar esta configuración, ya que representa un gran obstáculo para un atacante que logra conectarse a la red y quiere comprometer otros dispositivos conectados a la misma.

Cabe destacar que esta configuración puede limitar ciertas funcionalidades legítimas, por ejemplo, acceder a una impresora para imprimir documentos a través de la red Wi-Fi. En este tipo de casos deberá evaluarse si se desea priorizar la funcionalidad o la seguridad que aporta esta configuración.

#### Red oculta/SSiD oculto

Si bien activar esta configuración no aporta seguridad contra un atacante experimentado, ayuda a que nuestra red pase más desapercibida y agrega un obstáculo más a quien quiera ingresar de forma no autorizada. Hay que tener en cuenta que los usuarios legítimos que quieran ingresar deberán realizar algunos pasos extra, por lo que no es una configuración cómoda para utilizar en redes de invitados.

#### Desactivar WPS

WPS o Wi-Fi Protected Setup es un estándar impulsado por la Wi-Fi Alliance con el fin de facilitar a los usuarios la configuración de redes Wi-Fi. Actualmente su utilización esta desaconsejada, dado que se conocen serias vulnerabilidades en algunos mecanismos utilizados por este estándar que podrían ser utilizadas por un atacante para acceder fácilmente a la red. Por lo tanto, se aconseja buscar la configuración correspondiente y desactivar WPS.

#### Configurar una red de invitados

La mayoría de los routers hogareños más modernos ofrece la posibilidad de crear una red guest, también conocida como red de invitados. Básicamente, su objetivo es montar una red paralela a la principal con el fin de que allí se conecten todos los usuarios visitantes. Esta red generalmente podrá ser configurada con sus propios protocolos de seguridad, SSID, contraseña, etc. y es conveniente seguir la mayor cantidad posible de las recomendaciones aquí mencionadas.

[![](https://www.welivesecurity.com/wp-content/uploads/2019/12/eset-redes-publicas-privadas-01.jpg)](https://www.welivesecurity.com/wp-content/uploads/2019/12/eset-redes-publicas-privadas-01.jpg)

Ilustración que ejemplifica el resultado de crear una red de invitados para evitar la comunicación entre dispositivos confiables y no confiables.

Este ítem es extremadamente importante desde el punto de vista de la seguridad informática, ya que responde a uno de sus principios básicos: que cada usuario pueda [acceder únicamente a la mínima cantidad de recursos necesaria](https://www.welivesecurity.com/la-es/2018/07/02/principio-minima-exposicion-estrategia-seguridad/). Imaginemos la siguiente situación:

Organizamos una fiesta en nuestra casa e invitamos a muchos amigos, los cuales a su vez traen a sus amigos y otros acompañantes que no conocemos. Como todos ellos quieren acceder a Internet, compartimos la contraseña de nuestra red Wi-Fi.

Si no contamos con una red de invitados, todas estas personas a las cuales no conocemos tendrán acceso ilimitado a la red donde se encuentran nuestros dispositivos. Es decir, a la red donde podríamos tener información sensible, confidencial, donde realizamos actividades bancarias, etc. Esto representa un riesgo muy grande, ya que cualquiera de esas personas podría tener intenciones maliciosas y, aunque no realice ninguna en ese momento, podría volver más adelante y conectarse a nuestra red desde el exterior de nuestro domicilio sin que nosotros lo sepamos. Aun si todas estas personas fuesen totalmente confiables y bien intencionadas, no tenemos ninguna garantía de que sus dispositivos no hayan sido previamente comprometidos y estén siendo utilizados como una plataforma para lanzar nuevos ataques.

El principal beneficio de la red de invitados será separar y compartimentar a los dispositivos en los que confiamos de aquellos en los que no confiamos. Por lo tanto, esta configuración es fundamental para la seguridad de toda red hogareña (para el caso de redes corporativas hay configuraciones aún más sofisticadas).

#### Nombre de red genérico

Es muy conveniente, en complemento al ítem anterior, utilizar nombres de red genéricos que no puedan ser asociados a la ubicación, dirección, dueños o integrantes de la red. Si bien este punto no aporta seguridad en sí, sirve para casos en los que el atacante podría ser un vecino, alguien que nos conozca o alguien que esté intentando atacarnos de forma dirigida. Por ejemplo, si vivimos en un edificio y tenemos un vecino llamado Juan al cual conocemos; al observar que hay una red Wi-Fi llamada Red\_De\_Juan, uno podría intentar ingresar a esa red mediante un ataque que utilice contraseñas generadas a partir de información relacionada a Juan: fecha de cumpleaños, nombre de sus hijos, número de departamento, etc. (lo cual no sería posible si Juan hubiese utilizado las buenas prácticas de elección de contraseña). El fin de utilizar nombres de red genéricos es no aportar ningún tipo de información adicional a un eventual atacante.

#### ARP binding / Ligado ARP

Las tablas ARP sirven para asociar una dirección IP con una dirección MAC y son extremadamente necesarias para el funcionamiento de los protocolos de comunicación, por lo tanto, cada dispositivo de red cuenta con su propia tabla ARP y el router no es una excepción.

Como sabemos, el protocolo ARP sirve para comunicar información que luego será guardada en las tablas ARP. Sin embargo, este no realiza ningún tipo de autenticación o verificación de la integridad de la información que maneja, por lo que un atacante malicioso podría alterar arbitrariamente la información de dichas tablas. Esto es un gran problema de seguridad, ya que alterar esa información puede llevar a ataques de DoS, MITM, etc.

Dado que estas tablas pueden cambiar dinámicamente en base a la información recibida y que esta información podría ser maliciosa, una posible medida a tomar es definir tablas ARP donde algunas entradas sean estáticas y no cambien dinámicamente. Esta medida se conoce como ARP binding o “ligado ARP” y consiste en ligar una dirección MAC a una dirección IP de modo tal que esa entrada de la tabla no pueda ser modificada y, por ende, ninguna de las direcciones pueda ser asociada a otra dirección dinámicamente.

Por lo tanto, se aconseja ligar la dirección MAC de los dispositivos conocidos a su dirección IP con el fin de evitar que estos sean víctimas de ataques MITM u otros ataques basados en ARP poisoning.

#### Firewall y protección DoS

Muchos routers cuentan con funcionalidades como Firewall SPI y mecanismos de control de ataques DoS. El firewall SPI sirve para controlar el tráfico que pasa a través de la red, analizando el estado de las conexiones y sus características. En caso de encontrar trafico inusual o malicioso se toman medidas para detener o bloquear dichas comunicaciones. Es conveniente que esta funcionalidad este activada, ya que representa una medida más de protección contra un eventual atacante.

El control anti-DoS funciona monitoreando el tráfico en busca de floodings o inundaciones de paquetes, es decir, en busca de uno o más host que esté enviando una cantidad muy grande de paquetes en muy poco tiempo con el fin de saturar la red. Algunas variantes de ataques DoS que suelen ser contempladas en routers hogareños son:

*   ICMP flood: se inunda la red con paquetes ICMP.
*   UDP flood: se inunda la red con paquetes UDP.
*   SYN flood: se inunda la red con paquetes TCP SYN.

Usualmente, cuando se encuentra un host de la red llevando a cabo alguno de estos ataques se lo bloquea automáticamente.

Hay que considerar que, si bien esta funcionalidad también es muy positiva en cuanto a seguridad, según su configuración podría llegar a consumir muchos recursos del router. A su vez, si la red en cuestión es una red hogareña asegurada y controlada, este tipo de ataques podrían no ser tan usuales. Por lo tanto, será necesario tener en cuenta el costo/beneficio y, en caso de optar por utilizarla, estar atentos a la performance durante el proceso de configuración con el fin de encontrar una que no impacte negativamente.

#### Desactivar servicios no utilizados

Todos aquellos servicios o configuraciones que no sean utilizados deberían ser desactivados. Esto se debe a que cada servicio que abre un puerto, acepta conexiones del exterior o permite algún tipo de acceso puede transformarse en un eventual vector de ataque a nuestra red. Por lo tanto, cuanto menor sea la cantidad de servicios y puertos abiertos, también serán menores las opciones que tendrá un atacante para comprometer la red. Algunos ejemplos de esto son: UPnP, zonas DMZ, NAT forwarding, etc.

#### Actualizar firmware

Es una buena práctica mantener el firmware de nuestro router actualizado a la última versión. Esto es importante, ya que cuando se lanzan nuevas versiones los fabricantes suelen corregir fallas, agregar nuevas funcionalidades, mejorar las ya presentes y corregir [vulnerabilidades de seguridad](https://www.welivesecurity.com/la-es/2018/10/01/brasil-aprovechan-vulnerabilidad-en-routers-para-redirigir-usuarios-falsas-paginas-de-bancos/). Es importante destacar que las nuevas versiones del firmware deben ser descargadas exclusivamente del sitio oficial del fabricante del router, ya que de lo contrario no tenemos garantías de su integridad.  
  

Fuente: [https://www.welivesecurity.com/](https://www.welivesecurity.com/la-es/2019/12/16/guia-configurar-router-optimizar-seguridad-red-wi-fi/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)