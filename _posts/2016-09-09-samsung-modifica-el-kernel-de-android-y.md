---
title: 'Samsung modifica el kernel de Android y lo hace más inseguro'
date: 2020-02-17T03:12:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-cni8SJkrPfg/Xkn23Grb9LI/AAAAAAAALzo/NxYfMu7txFoHyiss6B5FntRpuM2Wh1nCQCLcBGAsYHQ/s400/google-on-your-smartphone-1796337_960_720.webp)](https://1.bp.blogspot.com/-cni8SJkrPfg/Xkn23Grb9LI/AAAAAAAALzo/NxYfMu7txFoHyiss6B5FntRpuM2Wh1nCQCLcBGAsYHQ/s1600/google-on-your-smartphone-1796337_960_720.webp)

  
Hace poco tiempo, los especialistas en **[análisis de vulnerabilidades](https://www.iicybersecurity.com/analisis-de-vulnerabilidad-informatica.html)** de Samsung anunciaron que implementarían una serie de modificaciones en el código del kernel Android, en un intento por prevenir algunas variantes de ataque comunes contra usuarios de los dispositivos Galaxy. 

  

A pesar de estos esfuerzos, los expertos de Google Project Zero revelaron que estas modificaciones terminaron por exponer los dispositivos a más inconvenientes de seguridad, por lo que han solicitado a **[Samsung](https://noticiasseguridad.com/hacking-incidentes/smartphones-samsung-galaxy-son-hackeados-para-extorsionar-a-las-victimas/)** y a otros fabricantes de dispositivos inteligentes usar las características de seguridad que ya existen, pues no se tiene control sobre las fallas que pueden originarse debido a estas modificaciones de kernel.

  

Acorde a Jann Horn, especialista en análisis de vulnerabilidades miembro de **[Project Zero](https://noticiasseguridad.com/tecnologia/como-hackear-un-iphone-en-tres-formas-diferentes-usando-vulnerabilidades-de-cero-clics/)**, este error (común entre los desarrolladores) consiste en agregar código al kernel de Linux en sentido descendente que los desarrolladores del kernel en sentido ascendente no han revisado. 

  

Si bien estas modificaciones están orientadas a la seguridad de los dispositivos, los desarrolladores en las compañías fabricantes no reparan en las fallas que estas ligeras alteraciones podrían generar en otras partes del sistema. En el caso de Samsung, las modificaciones generaron una falla de corrupción de memoria en el subsistema de seguridad llamado _Process Authenticator_. Esta falla fue reportada a Google y corregida en la actualización para dispositivos Galaxy correspondiente al mes de febrero.

  

Las actualizaciones para Galaxy del mes de febrero también incluían parches de seguridad para corregir una vulnerabilidad en los dispositivos con tecnología **Trusted Execution Environment** (TEE), un entorno de seguridad aislado en el procesador de cada dispositivo. Aún no se ha determinado si existe un vínculo entre las modificaciones hechas por Samsung y la presencia de esta falla. 

  

En su informe, los especialistas en análisis de vulnerabilidades de Project Zero afirman que la mayoría de las modificaciones del kernel hechas por Samsung son innecesarias y no afectarían el funcionamiento de los dispositivos Galaxy en caso de ser removidas. 

  

El Instituto Internacional de Seguridad Cibernética (IICS) menciona que las modificaciones de kernel podrían ser mejor implementadas si se actualizan o trasladan a controladores de espacio del usuario, donde puedan implementarse en lenguajes de programación más seguros o en entornos aislados, además de que dejarían de ser inconvenientes para versiones posteriores del kernel. 

  

Fuente: [https://noticiasseguridad.com/](https://noticiasseguridad.com/seguridad-movil/samsung-modifica-el-kernel-de-android-y-lo-hace-mas-inseguro/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)