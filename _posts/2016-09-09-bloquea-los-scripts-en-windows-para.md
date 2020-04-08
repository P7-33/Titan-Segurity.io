---
title: 'Bloquea los scripts en Windows para evitar el malware Emotet y otros'
date: 2019-10-13T00:08:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-aWR9uRKcZGg/XaJb2XlWlJI/AAAAAAAALG0/2wAemVuaajY1jYLO0CYUt9ejimGIpC9kACLcBGAsYHQ/s640/bloquear-scripts-windows-registro-650x340.jpg)](https://1.bp.blogspot.com/-aWR9uRKcZGg/XaJb2XlWlJI/AAAAAAAALG0/2wAemVuaajY1jYLO0CYUt9ejimGIpC9kACLcBGAsYHQ/s1600/bloquear-scripts-windows-registro-650x340.jpg)

Son muchas las amenazas que hay presentes en la red hoy en día. Muchos tipos de ataques que pueden comprometer nuestra privacidad y seguridad. Ahora bien, por suerte también podemos poner en práctica una serie de consejos interesantes para aumentar nuestra seguridad. Hoy vamos a hablar de ello. Vamos a explicar cómo bloquear los scripts en Windows para evitar, entre otras cosas, el malware Emotet. Así pondremos una capa extra de seguridad en nuestro sistema y podremos protegernos en caso de recibir diferentes tipos de ataques que puedan utilizar este método.

  

El riesgo de seguridad en la red
--------------------------------

Lo cierto es que Internet nos ofrece un amplio abanico de posibilidades en todos los sentidos. Esto también incluye un repertorio interesante para los ciberdelincuentes. Pueden hacer uso de múltiples plataformas y herramientas para llevar a cabo sus ataques. Normalmente requieren de la interacción del usuario, de la víctima. Sin embargo en otras ocasiones pueden basarse en vulnerabilidades o mala configuración del sistema.

Dentro de todas las posibilidades que tienen para llevar a cabo sus ataques, sin duda el correo electrónico se ha convertido en algo muy utilizado. Prácticamente todo el mundo tiene una cuenta de correo electrónico, ya sea a nivel personal o empresarial. Esto significa que los piratas informáticos pueden poner allí sus miras para atacar.

Entre otras cosas pueden adjuntar un simple archivo de Word que nos pide habilitar macros. Estas macros podrían habilitar diferentes tipos de ataques como es el causado por el malware Emotet. Si habilitamos ese contenido podríamos poner en riesgo nuestro sistema, nuestro dispositivo e incluso afectar a otros usuarios dentro de nuestra lista de contactos.

Lógicamente el principal consejo en este caso es nunca habilitar las macros en un archivo Word que recibamos. No importa quién nos lo ha enviado. Incluso aunque sea un usuario en el que confiamos, ya que podría tratarse de un ataque que previamente ha afectado a esa persona. Por tanto hay que tener siempre sentido común en estos casos y tener mucho cuidado con todo tipo de archivos adjuntos que recibamos a nuestra cuenta de correo electrónico.

Cómo bloquear los scripts en Windows
------------------------------------

Ahora bien, algo que podemos poner en práctica es bloquear los scripts en Windows a todos los usuarios. De esta forma podremos evitar problemas como lo que hemos mencionado de habilitar macros al recibir un correo.

El hecho de bloquear los scripts en Windows nos puede librar de ataques como el malware Emotet y otros similares. Por suerte simplemente hay que seguir una serie de pasos sencillos que vamos a explicar. Una vez realizados tendremos bloqueados los scripts en nuestro sistema operativo de Microsoft.

Para ello podemos utilizar el Registro de Windows. El primer paso es ir a Inicio, escribimos regedit y lo ejecutamos como administrador. Una vez estemos aquí hay que acceder a la ruta HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows Script Host. Es allí donde tendremos que cambiar el valor para bloquear los scripts.

[![](https://1.bp.blogspot.com/--dbAXqgayJI/XaJcAehg75I/AAAAAAAALG4/3YTi0QwUoiA3JNe3OAS-VBkAoOrG8rObgCLcBGAsYHQ/s640/bloquear-scripts-windows-768x432.jpg)](https://1.bp.blogspot.com/--dbAXqgayJI/XaJcAehg75I/AAAAAAAALG4/3YTi0QwUoiA3JNe3OAS-VBkAoOrG8rObgCLcBGAsYHQ/s1600/bloquear-scripts-windows-768x432.jpg)

  

Una vez lleguemos a esta ruta, a la cual podemos acceder simplemente pegando lo que hemos puesto, veremos un único documento. Allí hay hacer clic en Setting y crear un valor nuevo. Para ello hacemos clic con el botón derecho en un espacio en blanco, le damos a Nuevo y valor DWORD (32 bits). Le ponemos Activado y en el valor tendremos que poner 0. De esta forma estaremos bloqueando los scripts.

En definitiva, siguiendo estos pasos que hemos mencionado podemos mejorar la seguridad de nuestro sistema Windows. Una capa más para protegernos frente a posibles correos electrónicos con archivos Word peligrosos, por ejemplo. Así nos defenderemos de malware como Emotet y otros similares que pueden dañar el buen funcionamiento de nuestro equipo.

Por otra parte, más allá de esto que hemos mencionado, es importante siempre contar con software de seguridad. De esta forma podremos detectar otras variedades de malware que puedan poner en riesgo nuestro sistema. De la misma forma es importante también tener los equipos actualizados. A veces surgen vulnerabilidades que son aprovechadas por piratas informáticos para llevar a cabo sus ataques. A través de parches y actualizaciones de seguridad podemos corregir estos problemas.  
  

Fuente: [https://www.redeszone.net/](https://www.redeszone.net/tutoriales/seguridad/bloquear-scripts-windows/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)