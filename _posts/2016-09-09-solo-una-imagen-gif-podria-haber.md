---
title: 'Solo una imagen GIF podría haber pirateado tu teléfono Android usando
WhatsApp'
date: 2019-10-06T01:29:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-vKbUjeVzJNw/XZk0lSxbCEI/AAAAAAAALFY/vDrRg--nfbUW7MQeXFOz534-TXiUomcswCLcBGAsYHQ/s640/whatsapp-account-hacking.png)](https://1.bp.blogspot.com/-vKbUjeVzJNw/XZk0lSxbCEI/AAAAAAAALFY/vDrRg--nfbUW7MQeXFOz534-TXiUomcswCLcBGAsYHQ/s1600/whatsapp-account-hacking.png)

  

  
Una imagen vale más que mil palabras, pero un GIF vale más que mil imágenes.  
  
Hoy en día, los cortos clips de bucle, los GIF están en todas partes: en sus redes sociales, en sus tableros de mensajes, en sus chats, ayudando a los usuarios a expresar perfectamente sus emociones, haciendo reír a las personas y reviviendo lo más destacado.  
  
Pero, ¿qué sucede si un saludo GIF de aspecto inocente con un mensaje de Buenos días, Feliz cumpleaños o Feliz Navidad piratea su teléfono inteligente?  
  
Bueno, ya no es una idea teórica.  
  
WhatsApp ha parcheado recientemente una vulnerabilidad de seguridad crítica en su aplicación para Android, que permaneció sin parchear durante al menos 3 meses después de ser descubierta, y si se explotaba, podría haber permitido que los piratas informáticos remotos comprometan los dispositivos Android y potencialmente roben archivos y mensajes de chat.  
  
**Vulnerabilidad de ejecución remota de código de WhatsApp**  
  
La vulnerabilidad, rastreada como CVE-2019-11932, es un error de corrupción de memoria doblemente libre que en realidad no reside en el código de WhatsApp, sino en una biblioteca de análisis de imágenes GIF de código abierto que utiliza WhatsApp.  
  
**hackear cuenta de whatsapp**  
  
Descubierto por el investigador de seguridad vietnamita Pham Hong Nhat en mayo de este año, el problema conduce con éxito a ataques de ejecución remota de código, lo que permite a los atacantes ejecutar código arbitrario en dispositivos específicos en el contexto de WhatsApp con los permisos que la aplicación tiene en el dispositivo.  
  
    "La carga útil se ejecuta en el contexto de WhatsApp. Por lo tanto, tiene el permiso para leer la tarjeta SD y acceder a la base de datos de mensajes de WhatsApp", dijo el investigador a The Hacker News en una entrevista por correo electrónico.  
  
  
    "El código malicioso tendrá todos los permisos que tiene WhatsApp, incluida la grabación de audio, el acceso a la cámara, el acceso al sistema de archivos, así como el almacenamiento sandbox de WhatsApp que incluye una base de datos de chat protegida, etc."  
  
  
**¿Cómo funciona la vulnerabilidad de WhatsApp RCE?**  
  
WhatsApp utiliza la biblioteca de análisis en cuestión para generar una vista previa de los archivos GIF cuando los usuarios abren la galería de su dispositivo antes de enviar cualquier archivo multimedia a sus amigos o familiares.  
  
Por lo tanto, debe tenerse en cuenta que la vulnerabilidad no se activa al enviar un archivo GIF malicioso a una víctima; en su lugar, se ejecuta cuando la propia víctima simplemente abre el Selector de Galería de WhatsApp mientras intenta enviar cualquier archivo multimedia a alguien.

  
  
Para explotar este problema, todo lo que un atacante debe hacer es enviar un archivo GIF malicioso especialmente diseñado a un usuario Android objetivo a través de cualquier canal de comunicación en línea y esperar a que el usuario simplemente abra la galería de imágenes en WhatsApp.  
  
Sin embargo, si los atacantes desean enviar el archivo GIF a las víctimas a través de cualquier plataforma de mensajería como WhatsApp o Messenger, deben enviarlo como un archivo de documento en lugar de archivos adjuntos de medios, porque la compresión de imágenes utilizada por estos servicios distorsiona la carga maliciosa oculta en las imágenes.  
  
Como se muestra en una demostración de video de prueba de concepto que el investigador compartió con The Hacker News, la vulnerabilidad también se puede explotar para simplemente abrir un shell inverso de forma remota desde el dispositivo pirateado.  
  
**Aplicaciones, dispositivos y parches disponibles vulnerables**  
El problema afecta a las versiones 2.19.230 de WhatsApp y versiones anteriores que se ejecutan en Android 8.1 y 9.0, pero no funciona para Android 8.0 y versiones posteriores.  
  
    "En las versiones anteriores de Android, el doble-libre todavía podía activarse. Sin embargo, debido a las llamadas malloc del sistema después del doble-libre, la aplicación simplemente falla antes de llegar al punto en el que podríamos controlar el registro de la PC". El investigador escribe.  
  
Nhat le dijo a The Hacker News que informó la vulnerabilidad a Facebook, propietario de WhatsApp, a fines de julio de este año, y que la compañía incluyó un parche de seguridad en WhatsApp versión 2.19.244, lanzado en septiembre.  
  
Por lo tanto, para protegerse contra cualquier vulnerabilidad que rodee esta vulnerabilidad, se recomienda actualizar su WhatsApp a la última versión de Google Play Store lo antes posible.  
  
Además de esto, dado que la falla reside en una biblioteca de código abierto, también es posible que cualquier otra aplicación de Android que use la misma biblioteca afectada también pueda ser vulnerable a ataques similares.  
  
El desarrollador de la biblioteca GIF afectada, llamada Android GIF Drawable, también ha lanzado la versión 1.2.18 del software para parchear la vulnerabilidad doblemente libre.  
  
WhatsApp para iOS no se ve afectado por esta vulnerabilidad.  
  

Fuente: [https://thehackernews.com/](https://thehackernews.com/2019/10/whatsapp-rce-vulnerability.html)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)