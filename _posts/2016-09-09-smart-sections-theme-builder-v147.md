---
title: 'Smart Sections Theme Builder v1.4.7 – WPBakery Page Builder Addon'
date: 2020-01-10T10:31:00+01:00
draft: false
---

Estimados amigos de Inseguros.  
  
En el post de hoy vamos a volver a machacar al público con una característica básica de seguridad de los sistemas Microsoft como es la monitorización del registro.  
  
Todos los cambios de seguridad que solemos hacer por políticas o comandos suelen acabar en la base de datos de los Windows, el registro.  
  
  

[![](https://1.bp.blogspot.com/-EqWDfBVfGUs/XheWyiyx91I/AAAAAAAAGfQ/IYzmwdtDzw4D8TFWiSDmazZKN-JCBo_NACLcBGAsYHQ/s320/detective-1424831_1280.png)](https://1.bp.blogspot.com/-EqWDfBVfGUs/XheWyiyx91I/AAAAAAAAGfQ/IYzmwdtDzw4D8TFWiSDmazZKN-JCBo_NACLcBGAsYHQ/s1600/detective-1424831_1280.png)

  
  
Hemos hablado mucho de este tema por artículos en el blog, incluso abrí una r[ama en mi github](https://github.com/kinomakino/REG_KEYS_MONITOR/blob/master/claves) personal con algunas claves del registro que si o si deberías monitorizar.  
  
Pero para qué hacer esto? imagina que configuras:   
HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Control\\SecurityProviders\\WDigest DWORD ‘UseLogonCredential’ value 1   
  
Esto qué hace? habilita en un controlador el tipo de autenticación Wdigest para que cuando ejecuten Mimikatz en un proceso de compromiso las claves estén en claro, no haga falta crackearlas. Los malos lo hacen así !!! tu configuras mecanismos de defensa y ellos los cambian!!!  
  
Bien, la cuestión es que la gente piensa en cómo monitorizar las claves, y piensa en clientes, agentes, cómo las gestiono, como detecto esos cambios en mi SIEM.   
  
Por partes. Lo que vamos a ver en este artículo es como levantar un evento, una alerta, cada vez que alguien mire o cambie un valor de una clave del registro concreta. Nos aparecerá un log en el visor de eventos y listo. Otra cosa es cuando tengas ese evento, como transformarlo en un correo (hay mil artículos de como enviar correos con eventos) enviarlo a un SIEM, ELK o similar...  
  
Entonces, al lío. Como cualquier elemento de auditoria en sistemas Microsoft, hay dos partes: decirle al sistema que vamos a auditar acceso y/o error en el registro; el segundo paso es identificar qué ramas del registro queremos auditar.\*\*\*\*\* esto es igual para TODO en Active Directory\*\*\*\*\*\*  
  
Allá vamos. Vamos al editor de políticas de grupo y creamos una política con esta información:  
  
  

[![](https://1.bp.blogspot.com/-uVtN1KfpJAo/XheSODLjvOI/AAAAAAAAGeU/HiGN7aLGoD0SWoxN7GC1NVjKGN28jJmmgCLcBGAsYHQ/s400/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.37.11.png)](https://1.bp.blogspot.com/-uVtN1KfpJAo/XheSODLjvOI/AAAAAAAAGeU/HiGN7aLGoD0SWoxN7GC1NVjKGN28jJmmgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.37.11.png)

  
Ahora vamos a la rama del registro que queremos auditar y seteamos la configuración, es decir, que para TODOS, audite el uso de estos permisos.  
  
  

[![](https://1.bp.blogspot.com/-hPgFNAkHxhw/XheSfYC0L7I/AAAAAAAAGec/v6WLQxLs9UsQi2p4YYQiDPmD-tnyFWkfQCLcBGAsYHQ/s400/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.40.09.png)](https://1.bp.blogspot.com/-hPgFNAkHxhw/XheSfYC0L7I/AAAAAAAAGec/v6WLQxLs9UsQi2p4YYQiDPmD-tnyFWkfQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.40.09.png)

  
Entonces, seguro que habéis pensado... esta política tiene sentido para el servidor en el que se configura, ya que hemos ido localmente al registro a indicarle la rama concreta. BIEN !!! si no lo has pensado... lo entiendes? xD  
  
Para eso usamos la rama Registro de las GPO en las que nos permite realizar esto, indicar qué claves del registro y qué permisos tienen, así, podemos emplearlo para un grupo de servidores (Por OU o como quiera que apliques la directiva).  
  
  

[![](https://1.bp.blogspot.com/-aCp_yQvLpOQ/XheS9U7p2hI/AAAAAAAAGek/rJc5QwmQS_cSYv18lLldgB4JrfxSN-NPACLcBGAsYHQ/s400/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.43.03.png)](https://1.bp.blogspot.com/-aCp_yQvLpOQ/XheS9U7p2hI/AAAAAAAAGek/rJc5QwmQS_cSYv18lLldgB4JrfxSN-NPACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.43.03.png)

  
Bien, ya sabes como hacerlo. Pero en muchas ocasiones, cuando habla con alumnos de cursos y similar, me comentan que con estos artículos se aprende la teoría, la manera de hacerlo, pero no se termina de centrar.  
  
Me refiero a bien, pero ahora como lo haces, cómo lo mantienes. Te voy a dar unos tips o consejos.  
  
Lo suyo es que esto lo hagas en entornos de pruebas. No esto en concreto porque no tiene mayor relevancia, pero para otros casos quizás si. Lo importante es realizar una copia de seguridad. Es tan sencilla como botón derecho.  
  
  

[![](https://1.bp.blogspot.com/-ZRWnDtXexik/XheT0bl_q2I/AAAAAAAAGe4/wBNTDKi_hukNqZbwrF3xRREfFRu9LoEtACLcBGAsYHQ/s400/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.47.40.png)](https://1.bp.blogspot.com/-ZRWnDtXexik/XheT0bl_q2I/AAAAAAAAGe4/wBNTDKi_hukNqZbwrF3xRREfFRu9LoEtACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B20.47.40.png)

  
Ahora la cuestión es que para importar una GPO entre dominios, en el entorno de pruebas y producción, se hace con un pequeño hack. En el servidor destino creas la política, y le dices que importe la configuración de un backup. De esta manera se importa una GPO entre dominios.  
  
Bien, más trucos... Como he dicho, tengo una lista de claves del registro que me gustan, pero puede que tu tengas la tuya. Hay una manera cutre de importar estas claves de manera automática, y no tener que hacer el proceso 2 ( entrar en el registro, establecer permiso) pero no se la digas a nadie xD  
  
Localiza tu GPO en SYSVOL, en mi caso estaba aquí: \\\\miempresa.local\\SYSVOL\\miempresa.local\\Policies\\{5F23582A-A1BA-4D22-A34B-AB5B3C29307A}\\Machine\\Microsoft\\Windows NT\\SecEdit  
  
[El fichero es el mismo que teneis en mi github](https://github.com/kinomakino/REG_KEYS_MONITOR/blob/master/GptTmpl.inf), para que solo copies y pegueis so vagos !!!  
  
Como se aprecia, se identifica la rama del registro y la [SACL](https://www.windows-active-directory.com/microsoft-active-directory-objects-authentication-process.html#more-93)  
  
  

"USERS\\.DEFAULT\\Environment" ,0,"D:PAR(A;CI;KA;;;BA)(A;CIIO;KA;;;CO)(A;CI;KA;;;SY)(A;CI;KR;;;BU)(A;CI;KR;;;S-1-15-2-1)S:AR(AU;OICISA;CCDCLCSD;;;WD)"

"USERS\\.DEFAULT\\Software\\Classes\\Exefile\\Shell\\Runas\\Command\\IsolatedCommand" ,0,"D:PAR(A;CI;KA;;;BA)(A;CIIO;KA;;;CO)(A;CI;KA;;;SY)(A;CI;KR;;;BU)(A;CI;KR;;;S-1-15-2-1)S:AR(AU;OICISA;CCDCLCSD;;;WD)"

"USERS\\.DEFAULT\\Software\\Classes\\Mscfile\\Shell\\Open\\Command" ,0,"D:PAR(A;CI;KA;;;BA)(A;CIIO;KA;;;CO)(A;CI;KA;;;SY)(A;CI;KR;;;BU)(A;CI;KR;;;S-1-15-2-1)S:AR(AU;OICISA;CCDCLCSD;;;WD)"

Si editamoseste fichero y lo modificamos añadiendo tus claves de registro, podrás cargar más fácilmente tu lista.  

  

[![](https://1.bp.blogspot.com/-xafNPz25UFc/XheWFHMXUaI/AAAAAAAAGfE/gutBD3H5CGYYT96KZwQjvsdfuLfBzgZmQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.40.25.png)](https://1.bp.blogspot.com/-xafNPz25UFc/XheWFHMXUaI/AAAAAAAAGfE/gutBD3H5CGYYT96KZwQjvsdfuLfBzgZmQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.40.25.png)

  

Pero bueno, se nos olvida lo importante !!! Queremos ver cómo al hacer un cambio en la rama del registro nos aparece un evento...

  

[![](https://1.bp.blogspot.com/-U9qn7cZtbxM/XheWXuj-a8I/AAAAAAAAGfM/Xju3Sg4b3YMSvWR03g70iBWo6hwEtsNMACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.41.51.png)](https://1.bp.blogspot.com/-U9qn7cZtbxM/XheWXuj-a8I/AAAAAAAAGfM/Xju3Sg4b3YMSvWR03g70iBWo6hwEtsNMACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2020-01-09%2Ba%2Blas%2B21.41.51.png)

  

Ahora con ese evento, puedes configurar en tu SIEM, gestor de eventos o aparato mágico una alerta que te información si es un comportamiento normal, o es un "kinomakino" tocando tu Windows xDDD.

  

Espero que te sirva de ayuda y sobre todo, gracias por leerme !!!