---
title: 'Vulnerabilidad StrandHogg es una amenaza para dispositivos Android y ya
está bajo ataque'
date: 2019-12-04T02:51:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-cthYScV9I7o/XecRBP6q43I/AAAAAAAALbI/xA1lQzmtqy0UxlrsTMZa5JI2BJ0f01ZuQCLcBGAsYHQ/s640/StrandHogg-384x220.jpg)](https://1.bp.blogspot.com/-cthYScV9I7o/XecRBP6q43I/AAAAAAAALbI/xA1lQzmtqy0UxlrsTMZa5JI2BJ0f01ZuQCLcBGAsYHQ/s1600/StrandHogg-384x220.jpg)

  
Los expertos de la compañía noruega Promon [descubrieron una vulnerabilidad en Android](https://promon.co/security-news/strandhogg/) que permite que las aplicaciones maliciosas modifiquen legítimas y realicen operaciones maliciosas en su nombre.

Una vulnerabilidad llamada StrandHogg podría engañar a un usuario para que otorgue privilegios peligrosos a una aplicación maliciosa, y cuando el usuario interactúa legítimamente con la aplicación. Además, el error se puede usar para mostrar a las víctimas páginas de inicio de sesión falsas mientras se conecta a aplicaciones legítimas.

Según los expertos, el problema ya está siendo utilizado por los atacantes. Por lo tanto, se descubrió una vulnerabilidad cuando una compañía de seguridad del sector financiero de Europa del Este no identificada recurrió a Promon en busca de ayuda, ya que varios bancos en la República Checa informaron que el dinero había desaparecido de las cuentas de los clientes. El socio de Europa del Este proporcionó a los investigadores una muestra para el análisis, y pudieron detectar el problema StrandHogg.

Los analistas de Promon, junto con expertos de Lookout, descubrieron que la vulnerabilidad explotaba al menos 36 aplicaciones maliciosas. Los investigadores no revelan sus nombres, pero enfatizan que ninguna de las aplicaciones se distribuyó directamente a través del catálogo oficial de Google Play Store. Con mayor frecuencia, las aplicaciones cayeron en los dispositivos de los usuarios como cargas de la segunda etapa del ataque, es decir, las víctimas primero descargaron e instalaron otro malware de Play Store.

Hablando sobre el aspecto técnico del asunto, la vulnerabilidad raíz de StrandHogg es cómo Android cambia entre diferentes procesos que están asociados con diferentes operaciones y aplicaciones. En esencia, el problema de StrandHogg radica en el componente responsable de la multitarea. Como resultado, cuando un usuario inicia una aplicación legítima, el malware tiene la oportunidad de usar StrandHogg para ejecutar código malicioso, utilizando, por ejemplo, taskAffinity y allowTaskReparenting.

Entonces, el usuario inicia una aplicación legítima, pero el código se ejecuta desde un código malicioso. Dicho código puede solicitar derechos peligrosos o mostrar páginas de phishing. Dado que todo esto sucede después de hacer clic en el ícono de una aplicación legítima, el usuario asumirá que la solicitud de la pantalla correcta o de inicio de sesión también fue creada por esta aplicación y es poco probable que sospeche una suplantación de identidad.

[![](https://xakep.ru/wp-content/uploads/2019/12/251712/android-task-hijacking-vulnerability.png#26759185)](https://xakep.ru/wp-content/uploads/2019/12/251712/android-task-hijacking-vulnerability.png#26759185)

Según Promon, StrandHogg no requiere acceso de root y funciona en todas las versiones de Android, incluida la última versión de Android 10. Además, los expertos verificaron las 500 aplicaciones más populares de Google Play Store y descubrieron que los procesos de estas aplicaciones podrían verse comprometidos con StrandHogg y se usa para realizar acciones maliciosas.

Los investigadores escriben que notificaron a los ingenieros de Google sobre el problema el verano pasado, sin embargo, la vulnerabilidad no se solucionó en los 90 días prescritos.

  
Fuente: [https://xakep.ru/](https://xakep.ru/2019/12/03/strandhogg/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)