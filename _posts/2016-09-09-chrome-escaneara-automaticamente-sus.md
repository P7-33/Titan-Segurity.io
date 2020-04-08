---
title: 'Chrome escaneará automáticamente sus contraseñas contra violaciones de
datos'
date: 2019-12-16T00:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-HU9rgF6CwHw/XfbC85Q6QVI/AAAAAAAALfI/d_4eJZJ8p1Y_T43X9WgwG4b9Kd84X_FYACLcBGAsYHQ/s400/browser-773216_960_720.jpg)](https://1.bp.blogspot.com/-HU9rgF6CwHw/XfbC85Q6QVI/AAAAAAAALfI/d_4eJZJ8p1Y_T43X9WgwG4b9Kd84X_FYACLcBGAsYHQ/s1600/browser-773216_960_720.jpg)

  
La función de verificación de contraseña de Google se integrará completamente en las versiones de escritorio y móviles de Chrome 79.  
  
La función de comprobación de contraseña de Google se ha extendido lentamente por el ecosistema de Google el año pasado. Comenzó como la extensión "Password Checkup" para las versiones de escritorio de Chrome, que auditaría contraseñas individuales cuando las ingresó, y varios meses después se integró en cada cuenta de Google como una auditoría a pedido que puede ejecutar en todas sus contraseñas guardadas . Ahora, en lugar de una extensión de Chrome, Password Checkup se está integrando en las versiones de escritorio y móviles de Chrome 79.  
  
Todas estas funciones de verificación de contraseña funcionan para personas que tienen sus combinaciones de nombre de usuario y contraseña guardadas en Chrome y las sincronizan con los servidores de Google. Google calcula que, dado que tiene una gran base de datos (encriptada) de todas sus contraseñas, también podría compararlas con una lista pública de 4.000 millones de nombres de usuario y contraseñas comprometidos que han estado expuestos a innumerables violaciones de seguridad a lo largo de los años. Cada vez que Google llega a una coincidencia, le notifica que un conjunto específico de credenciales es público e inseguro y que probablemente debería cambiar la contraseña.  
  
El punto principal de esto es la seguridad, por lo que Google está haciendo todo esto al comparar sus credenciales cifradas con una lista cifrada de credenciales comprometidas. Chrome primero envía un hash cifrado de 3 bytes de su nombre de usuario a Google, donde se compara con la lista de nombres de usuario comprometidos de Google. Si hay una coincidencia, su computadora local recibe una base de datos de cada nombre de usuario y contraseña potencialmente coincidentes en la lista de credenciales incorrectas, encriptada con una clave de Google. Luego obtiene una copia de sus contraseñas cifradas con dos claves: una es su clave privada habitual y la otra es la misma clave utilizada para la lista de credenciales malas de Google. En su computadora local, Password Checkup elimina la única clave que puede descifrar, su clave privada, dejando su nombre de usuario y contraseña cifrados con la clave de Google, que se pueden comparar con la base de datos cifrada con claves de Google de credenciales malas. Google dice que esta técnica, llamada "intersección de conjunto privado", significa que no puede ver la lista de credenciales malas de Google, y Google no puede aprender sus credenciales, pero las dos se pueden comparar para las coincidencias.  
  
La creación de la verificación de contraseña en Chrome debería hacer que la auditoría de contraseñas sea más convencional. Solo las personas más conscientes de la seguridad buscarían e instalarían la extensión de Chrome o realizarían la auditoría de contraseña completa en passwords.google.com, y estas personas probablemente tengan una mejor higiene de contraseña para comenzar. La creación de la función en Chrome la colocará frente a los usuarios más convencionales que generalmente no consideran la seguridad de la contraseña, que son exactamente el tipo de personas que necesitan este tipo de cosas. Esta es también la primera vez que la verificación de contraseña está disponible en dispositivos móviles, ya que Chrome aún no admite extensiones (Google, por favor).  
  
Google dice: "Por ahora, estamos implementando esto gradualmente para todos los que hayan iniciado sesión en Chrome como parte de nuestras protecciones de Navegación segura". Los usuarios pueden controlar la función en la sección "Sincronización y servicios de Google" de la Configuración de Chrome, y si no ha iniciado sesión en Chrome y no sincroniza sus datos con los servidores de Google, la función no funcionará.  
  
Con Password Checkup integrado en Chrome, la extensión ya no es realmente útil. La versión web sigue siendo excelente como una auditoría de contraseña completa para todas sus contraseñas almacenadas por Google, y ahora la versión integrada en Chrome verificará continuamente sus contraseñas a medida que las ingrese.  
  

Fuente: [https://www.wired.com/](https://www.wired.com/story/chrome-79-password-check/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)