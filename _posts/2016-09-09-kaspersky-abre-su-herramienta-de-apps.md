---
title: 'Kaspersky abre su herramienta de apps Android a desarrolladores móviles'
date: 2020-01-22T22:53:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-QlwC5sr0sOU/XijEHcSBU9I/AAAAAAAALqc/rEkD681eJDErUZcmAIicuCdKwu9SW43kACLcBGAsYHQ/s640/malware-movil-android-1068x562.jpg)](https://1.bp.blogspot.com/-QlwC5sr0sOU/XijEHcSBU9I/AAAAAAAALqc/rEkD681eJDErUZcmAIicuCdKwu9SW43kACLcBGAsYHQ/s1600/malware-movil-android-1068x562.jpg)

  

Kaspersky ha [hecho público el acceso](https://github.com/KasperskyLab/Kaspresso) a Android Automated Testing Framework. La herramienta, denominada Kaspresso, utiliza una configuración flexible y fácil de usar. Con Kaspresso, los desarrolladores de aplicaciones móviles pueden reducir significativamente la cantidad de tiempo que necesitan para probar las aplicaciones sin el riesgo de pasar por alto un error, lo que acelera el proceso de lanzamiento de las aplicaciones. La herramienta ya ha recibido comentarios positivos en dos importantes conferencias tecnológicas: Mobilization IX y Codemotion Berlin 2019.

Para los desarrolladores de [aplicaciones móviles](https://revistabyte.es/movilidad/usamos-el-movil/) es todo un reto elegir una herramienta de pruebas automatizada que reduzca el tiempo de lanzamiento de sus apps. Hoy en día, existen muchos marcos de trabajo y herramientas para realizar pruebas automatizadas, como Espresso y Appium. Sin embargo, estos no pueden resolver todos los problemas que se encuentran los desarrolladores de Android, como los relacionados con los tests UI en cuanto a legibilidad, descentralización, registro y arquitectura.

### Kaspersky ha introducido una nueva herramienta para aplicaciones Android, llamada Kaspresso

Los problemas mencionados anteriormente impiden que los desarrolladores móviles realicen pruebas de interfaz de usuario limpias, estables, sostenibles y comprensibles. Para resolver los problemas existentes en las pruebas de IU, Kaspersky ha introducido una nueva herramienta para aplicaciones Android, llamada Kaspresso. La herramienta se basa en dos librerías para crear pruebas automatizadas de Android: Espresso y Kakao.

Gracias a la incorporación de la libreria Kakao, que funciona como wrapper DSL sobre Espresso, Kaspresso mejora la legibilidad de las pruebas IU, lo que lleva las descripciones de las pruebas a un nuevo nivel y las hace más comprensibles.

Kaspresso también resuelve el problema de los test granulares (Flaky tests) y el [registro](https://dzone.com/articles/why-dont-mobile-app-developers-use-logs). Los tests granulares son casos en los que el resultado de la prueba es impredecible y existen diferentes motivos para cada fallo, a pesar de que la funcionalidad trabaje sin problemas en el dispositivo del desarrollador. En cuanto al registro, la nueva herramienta muestra todas las actividades de Espresso. Además, el usuario puede modificarlo a posteriori.

Así, esta herramienta proporciona una manera sencilla y cómoda de gestionar los interceptores, que son el punto de entrada para todas las llamadas a las API que realizan los test. Kaspresso presenta un amplio conjunto de interceptores predeterminados para el manejo de los flaky test y la mejora del proceso de registro.

Finalmente, Kaspresso ofrece las mejores prácticas que los desarrolladores móviles de Kaspersky han adquirido tras muchos años de experiencia. El framework incluye recomendaciones de arquitectura para unificar y estandarizar las pruebas de IU.

«Decidimos poner a disposición del público el framework de Kaspresso, ya que la creación de este tipo de herramientas para autopruebas requiere mucho esfuerzo y recursos. Además, las herramientas de autotest para Android simplifican la labor de los desarrolladores móviles. Intentamos combinar los mejores recursos y prácticas en una sola herramienta y poner en ella nuestras mejores prácticas y experiencia. Esperamos que con la ayuda de Kaspresso, los desarrolladores móviles puedan crear aplicaciones Android mejores y más seguras. Estamos seguro de que los usuarios y toda la industria se beneficiarán de esto», comenta Victor Yablokov, director de Desarrollo de Productos Móviles de Kaspersky.

Fuente: [https://revistabyte.es/](https://revistabyte.es/seguridad-informatica/kaspersky-apps-android/)

No olvides Compartir... 

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)