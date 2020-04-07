---
title: 'Descubren vulnerabilidad en Apache Tomcat'
date: 2020-01-27T02:33:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-zK-OR66duQ4/Xi49y2Yvb5I/AAAAAAAALsE/t0w49TR2H9cpvZD4_HLIJ0kvU4GO1XM4wCLcBGAsYHQ/s640/Screenshot_20190415_145107-1.png)](https://1.bp.blogspot.com/-zK-OR66duQ4/Xi49y2Yvb5I/AAAAAAAALsE/t0w49TR2H9cpvZD4_HLIJ0kvU4GO1XM4wCLcBGAsYHQ/s1600/Screenshot_20190415_145107-1.png)

  

Especialistas en **[análisis de vulnerabilidades](https://www.iicybersecurity.com/analisis-de-vulnerabilidad-informatica.html)** han revelado el hallazgo de una nueva vulnerabilidad en **[Apache Tomcat](https://noticiasseguridad.com/vulnerabilidades/vulnerabilidad-de-ejecucion-remota-de-codigo-en-apache-tomcat/)**. Al usar la autenticación con Apache Tomcat, entre las versiones 9.0.0.M1 a 9.0.29, 8.5.0 a 8.5.49 y 7.0.0 a 7.0.98, se presenta una ventana estrecha por donde un actor de amenazas podría desplegar un ataque de fijación de sesión. 

  

Al inicio los investigadores consideraron que esta ventana era demasiado estrecha para funcionar como exploit en la práctica, no obstante, se decidió reportar este escenario como una falla de seguridad, registrada como CVE-2019-17563.

  

En el reporte de los expertos en análisis de vulnerabilidades, la conjunción de diversas circunstancias permite que se presente una condición de carrera en Tomcat, lo que permite la fijación de la sesión y, potencialmente, permitiría a los hackers realizar un ataque local para acceder a la sesión de un usuario con privilegios de administrador. 

  

Para más detalles, los expertos de la firma de seguridad Support Five han preparado un cuadro donde los administradores pueden consultar si sus productos o versiones ya han sido evaluados para esta falla. Para determinar si su versión es vulnerable, además si los componentes están afectados por la vulnerabilidad, y para obtener información sobre las versiones, las versiones puntuales o las revisiones que abordan la **[vulnerabilidad](https://noticiasseguridad.com/seguridad-informatica/%ef%bb%bfprograma-de-recompensas-de-vulnerabilidades-en-software-de-codigo-abierto/)**, consulte la siguiente tabla:

  
  
  

![](https://noticiasseguridad.com/nsnews_u/2020/01/tomcat.jpg)

En caso de que ejecute una versión afectada, los especialistas en análisis de vulnerabilidades del Instituto Internacional de Seguridad Cibernética (IICS) recomiendan corregir la falla actualizando a una de las versiones que cuentan con las soluciones. Si en la tabla se muestra solamente una versión anterior a la que está usted ejecutando actualmente, o no se menciona una versión vulnerable, no existe ninguna actualización por el momento.   

  

Para obtener más información sobre fallas de seguridad, exploits, ataques cibernéticos y análisis de malware encontrados recientemente, puede visitar el sitio web oficial del Instituto Internacional de Seguridad Cibernética (IICS), además de las plataformas de comunicación oficiales de las compañías tecnológicas que actualmente trabajan por corregir incidentes de seguridad informática.  
  

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/vulnerabilidades/descubren-vulnerabilidad-en-apache-tomcat/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)