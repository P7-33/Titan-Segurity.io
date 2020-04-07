---
title: 'USB Raw Gadget, un módulo para el Kernel que permite emular
dispositivos USB'
date: 2020-02-16T03:13:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Y7OOt9uM12Y/XkilFdNfmxI/AAAAAAAALzA/tjFtLgOdmsgHMYKX_rIiGVluBfqgew11QCLcBGAsYHQ/s640/USB-Raw-Gadget.jpeg)](https://1.bp.blogspot.com/-Y7OOt9uM12Y/XkilFdNfmxI/AAAAAAAALzA/tjFtLgOdmsgHMYKX_rIiGVluBfqgew11QCLcBGAsYHQ/s1600/USB-Raw-Gadget.jpeg)

  

Ya en algunas ocasiones **aquí en el blog hemos hablado sobre los trabajos realizados por parte de Andrey Konovalov** (un desarrollador de Google) en Linux, desde su trabajo en la detección oportuna de fallos en los controladores USB del Kernel de Linux y también en dispositivos Wifi.

  

**Ahora en estos momentos él se encuentra trabajando en** el desarrollo de un nuevo módulo para el Kernel de Linux el cual ha nombrado como **“USB Raw Gadget”** el cual describe como una utilidad que permite emular dispositivos USB en el espacio del usuario.

  

Además de que **menciona que se está considerando una aplicación para la inclusión de este módulo en el núcleo principal de Linux.** Por su parte Google Raw Gadget ya está siendo utilizado por Google para simplificar las pruebas difusas de la pila del kernel USB con el kit de herramientas syzkaller.

Inicialmente estaba usando GadgetFS (junto con el módulo Dummy HCD / UDC) para realizar la emulación de dispositivos USB para fuzzing, pero luego se cambió a una nterfaz escrita personalizada.

  

El incentivo para implementar una interfaz diferente era proporcionar un acceso directo y algo en bruto a la capa Gadget USB para el espacio de usuario, donde cada solicitud USB se pasa al espacio de usuario para obtener una respuesta.

Sobre USB Raw Gadget
--------------------

**El módulo se encarga de agregar una nueva interfaz** de programación **al subsistema del kernel** llamada “USB Gadget” y que se está desarrollando como una alternativa a GadgetFS.

**La creación de una nueva API se debe a la necesidad de obtener acceso directo y de bajo nivel** al subsistema Gadget USB desde el espacio del usuario, lo que permite procesar todas las solicitudes USB posibles (GadgetFS procesa algunas solicitudes por sí solo, sin transferirlo al espacio del usuario).

**USB Raw Gadget se controla a través del dispositivo /dev/raw-gadget** por analogía con /dev/gadget en GadgetFS, pero se utiliza una interfaz basada en ioctl(), en lugar de un pseudo-FS, para la interacción.

Además del procesamiento directo de todas las solicitudes de USB por un proceso en el espacio del usuario, la nueva interfaz también tiene la capacidad de devolver cualquier dato en respuesta a una solicitud de USB (GadgetFS verifica la exactitud de los descriptores de USB y filtra ciertas respuestas, lo que interfiere con la detección de errores durante la prueba de borrado de la pila USB).

**USB Raw Gadget también permite seleccionar un dispositivo UDC específico** (controlador de dispositivo USB) y un controlador para conectar, mientras que GadgetFS se conecta al primer dispositivo UDC disponible.

Para diferentes UDC, los nombres de puntos finales predecibles se asignan a diferentes tipos de canales de comunicación separados dentro de un solo dispositivo.

Finalmente, si quieres conocer más al respecto, puedes consultar los detalles, así como el log de los cambios realizados en USB Raw Gadget [en el siguiente enlace.](https://lwn.net/Articles/809448/)

¿Cómo instalar el módulo USB Raw Gadget en Linux?
-------------------------------------------------

Para quienes estén interesados en poder probar este modulo en su sistema, podrán hacerlo siguiendo las instrucciones que se detallan aquí.

**Para Dummy HCD/UDC** (un módulo que configura dispositivos USB virtuales y controladores de host que están conectados entre sí dentro del núcleo). **Debemos abrir una terminal y en ella vamos a teclear el siguiente comando:**

1

`svn checkout [https://github.com/xairy/raw-gadget/trunk/dummy_hcd](https://github.com/xairy/raw-gadget/trunk/dummy_hcd)`

Con ello vamos a obtener la carpeta con los módulos los cuales vamos a compilar ejecutando en la terminal el siguiente comando:

1

2

3

`cd dummy_hcd`

`make`

Y procedemos a instalarlos con:

1

`./insmod.sh`

En caso de querer actualizar el módulo lo hacemos con:

1

`./update.sh`

Ahora **para quienes quieran instalar el modulo del kernel**. En una terminal vamos a obtener los archivos necesarios para ello ejecutando el siguiente comando:

1

`svn checkout [https://github.com/xairy/raw-gadget/trunk/raw_gadget](https://github.com/xairy/raw-gadget/trunk/raw_gadget)`

Con ello vamos a obtener la carpeta con los módulos los cuales vamos a compilar ejecutando en la terminal el siguiente comando:

1

2

3

`cd dummy_hcd`

`make`

**Y procedemos a instalarlos con:**

1

`./insmod.sh`

En caso de querer actualizar el módulo lo hacemos con:

1

`./update.sh`

Puedes consultar el trabajo en [el siguiente enlace. ](https://github.com/xairy/raw-gadget)

  

Fuente: [https://www.linuxadictos.com/](https://www.linuxadictos.com/usb-raw-gadget-un-modulo-para-el-kernel-que-permite-emular-dispositivos-usb.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)