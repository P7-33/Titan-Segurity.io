---
title: 'El error crítico de Bluetooth en Android no requiere la interacción del
usuario'
date: 2020-02-07T23:22:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-GcnsGTutovQ/Xj3itRDLZVI/AAAAAAAALwE/pkcGBB-Nm0gw8VLugqks30wyA8WQrHPfACLcBGAsYHQ/s400/AndroidBT-384x220.jpg)](https://1.bp.blogspot.com/-GcnsGTutovQ/Xj3itRDLZVI/AAAAAAAALwE/pkcGBB-Nm0gw8VLugqks30wyA8WQrHPfACLcBGAsYHQ/s1600/AndroidBT-384x220.jpg)

Los desarrolladores de Google lanzaron [actualizaciones de febrero](https://source.android.com/security/bulletin/2020-02-01) para Android esta semana . Entre ellos se encuentra una solución para una vulnerabilidad crítica en el componente Bluetooth del sistema operativo. Según los expertos en seguridad de la información, este problema se puede utilizar sin ninguna interacción con el usuario, incluida la creación de gusanos Bluetooth autopropagantes.

La vulnerabilidad recibió el identificador  [CVE-2020-0022](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-0022)  y fue descubierta por especialistas de la empresa alemana [ERNW](https://insinuator.net/2020/02/critical-bluetooth-vulnerability-in-android-cve-2020-0022/) . El error se reprodujo en Android 8 y 9, pero los investigadores están seguros de que las versiones anteriores del sistema operativo también son vulnerables. CVE-2020-0022 no funciona solo contra Android 10 (provoca que solo el daemon Bluetooth se bloquee).

Para resolver el problema, no necesita ninguna interacción con el usuario, es suficiente que Bluetooth esté habilitado en el teléfono de la víctima. Cabe señalar que las versiones modernas del sistema operativo Android vienen con Bluetooth habilitado de forma predeterminada, y muchos usuarios usan auriculares Bluetooth, es decir, Bluetooth actualmente está habilitado en muchos dispositivos.

Los expertos de ERNW escriben que la vulnerabilidad permite que un atacante ejecute silenciosamente código arbitrario con los privilegios de un demonio Bluetooth. De hecho, el atacante solo necesita conocer la dirección MAC de Bluetooth del dispositivo de destino, que en algunos casos se puede determinar a través de la dirección MAC de Wi-Fi. En caso de un ataque exitoso, un atacante podrá robar los datos personales de la víctima, y ​​potencialmente se puede explotar un error para propagar el malware a través de Bluetooth.

Los investigadores planean publicar detalles técnicos y una vulnerabilidad para esta vulnerabilidad más adelante, pero por ahora les dan tiempo a los usuarios para instalar actualizaciones.

  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2020/02/07/bluetooth-wormable-bug/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)