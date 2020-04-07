---
title: 'Lista de credenciales encontrada para 500,000 servidores, enrutadores y
dispositivos IoT'
date: 2020-01-20T14:39:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-2QisrzneBY4/XiWtU2s_DiI/AAAAAAAALp0/dHEBjeNv3GY5OEFQJoNifVo_QHKuDBVFACLcBGAsYHQ/s640/IoT-384x220.jpg)](https://1.bp.blogspot.com/-2QisrzneBY4/XiWtU2s_DiI/AAAAAAAALp0/dHEBjeNv3GY5OEFQJoNifVo_QHKuDBVFACLcBGAsYHQ/s1600/IoT-384x220.jpg)

Se ha publicado recientemente una lista extensa de 515.000 cuentas de datos de Telnet a varios servidores, routers y diversos dispositivos inteligentes. El volcado incluye direcciones IP de dispositivos, nombres de usuario y contraseñas, así como información de protocolo que se puede utilizar para controlar dispositivos de forma remota.

La lista se hizo pública por un operador de botnets DDoS autónomo que afirma haberla compilado por su cuenta, escaneando Internet en busca de dispositivos mal protegidos accesibles a través de Telnet. Para acceder a ellos, el operador utilizó las credenciales predeterminadas o las combinaciones de usuarios de nombres de usuario y contraseñas que son fáciles de adivinar. La información tiene fecha de octubre a noviembre de 2019.

[![](https://xakep.ru/wp-content/uploads/2020/01/264130/iot-list-files.png#26759185)](https://xakep.ru/wp-content/uploads/2020/01/264130/iot-list-files.png#26759185)

Respondiendo a la pregunta de por qué publicar una lista tan grande de bots en el dominio público, el autor del volcado respondió que había actualizado recientemente su servicio DDoS y que ahora no funciona con IoT-bonnet, sino que depende del alquiler de servidores de alto rendimiento de proveedores de servicios en la nube. Es decir, ya no necesita una lista.

Mediante los motores de búsqueda IoT (BinaryEdge y Shodan), los reporteros de ZDNet pudieron recopilar información sobre los dispositivos de la lista. Algunos de ellos se encuentran en las redes de proveedores de Internet conocidos (obviamente, estos son enrutadores y dispositivos IoT), pero otros se vieron en las redes de grandes proveedores de servicios en la nube.

Los expertos en seguridad sin nombre con los que hablaron los reporteros de ZDNet advirtieron que una lista fusionada en la red aún podría ser peligrosa, incluso si algunos de los datos ya no eran válidos (en los últimos meses, los dispositivos podrían cambiar su dirección IP y contraseña). El hecho es que los dispositivos configurados incorrectamente generalmente se distribuyen de manera desigual en la red, pero a menudo se ubican de forma masiva en la red de un proveedor, ya que durante el despliegue, su personal configura de forma masiva los dispositivos incorrectamente. Como resultado, el atacante tiene la oportunidad de usar las direcciones IP de la lista publicada para determinar el proveedor, y luego volver a escanear su red con más cuidado, agregando nuevas víctimas a la lista.

  
  

Fuente: [https://xakep.ru/](https://xakep.ru/2020/01/20/iot-credentials/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)