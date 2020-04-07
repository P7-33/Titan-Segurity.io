---
title: 'Más de 500 extensiones de Chrome cargan datos privados en secreto'
date: 2020-02-17T16:53:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-unmBF8TOWF4/Xkq2QtxjXUI/AAAAAAAALz0/D9qtHm47mg8E7aJzwO17xS5Tl1On4BtQwCLcBGAsYHQ/s640/security-top_art-chrome%25252520extensions%25252520private%25252520data-905814964.jpg)](https://1.bp.blogspot.com/-unmBF8TOWF4/Xkq2QtxjXUI/AAAAAAAALz0/D9qtHm47mg8E7aJzwO17xS5Tl1On4BtQwCLcBGAsYHQ/s1600/security-top_art-chrome%25252520extensions%25252520private%25252520data-905814964.jpg)

ILLUSTRATION: CASEY CHIN

  

Un investigador descubrió que cientos de extensiones en la tienda web eran parte de un esquema de publicidad y fraude publicitario de larga duración.

  

Más de 500 extensiones de navegador descargadas millones de veces de Chrome Web Store de Google subieron datos privados de navegación a servidores controlados por atacantes, dijeron investigadores el jueves.

  

Las extensiones formaron parte de un esquema de publicidad y fraude publicitario de larga data que fue descubierto por el investigador independiente Jamila Kaya. Ella y los investigadores de Duo Security, propiedad de Cisco, finalmente identificaron 71 extensiones de Chrome Web Store que tenían más de 1.7 millones de instalaciones. Después de que los investigadores informaron en privado sus hallazgos a Google, la compañía identificó más de 430 extensiones adicionales. Desde entonces, Google ha eliminado todas las extensiones conocidas.

  

"En el caso reportado aquí, los creadores de extensiones de Chrome habían hecho específicamente extensiones que ofuscaron la funcionalidad publicitaria subyacente de los usuarios", escribieron en un informe Jacob Rickerd, investigador de Kaya y Duo Security. "Esto se hizo para conectar a los clientes del navegador a una arquitectura de comando y control, filtrar datos de navegación privados sin el conocimiento de los usuarios, exponer al usuario al riesgo de explotación a través de flujos de publicidad e intentar evadir los mecanismos de detección de fraude de Chrome Web Store . "

  

**Un laberinto de redireccionamientos, malware y más**

  

Las extensiones se presentaron principalmente como herramientas que proporcionaban varias utilidades de promoción y publicidad como servicio. De hecho, se involucraron en fraude publicitario y publicidad maliciosa al barajar los navegadores infectados a través de un laberinto de dominios incompletos. Cada complemento se conectó primero a un dominio que usaba el mismo nombre que el complemento (por ejemplo: Mapstrek \[.\] Com o ArcadeYum \[.\] Com) para verificar si hay instrucciones para desinstalarse.

  

Luego, los complementos redirigieron los navegadores a uno de los pocos servidores de control codificados para recibir instrucciones adicionales, ubicaciones para cargar datos, listas de fuentes de publicidad y dominios para futuras redirecciones. Los navegadores infectados luego cargaron los datos del usuario, actualizaron las configuraciones de los complementos y fluyeron a través de un flujo de redirecciones del sitio.

  

El informe del jueves continuó:

  

> El usuario recibe regularmente nuevos dominios redireccionadores, ya que se crean en lotes, y se crean múltiples de los dominios anteriores en el mismo día y hora. Todos operan de la misma manera, reciben la señal del host y luego los envían a una serie de secuencias de anuncios y, posteriormente, a anuncios legítimos e ilegítimos. Algunos de estos se enumeran en la sección "Dominios finales" de los COI, aunque son demasiado numerosos para enumerarlos.

  

Muchas de las redirecciones llevaron a anuncios benignos para productos de Macy's, Dell y Best Buy. Lo que hizo que el esquema fuera malicioso y fraudulento fue (a) el gran volumen de contenido del anuncio (hasta 30 redirecciones en algunos casos), (b) la ocultación deliberada de la mayoría de los anuncios de los usuarios finales y (c) el uso del anuncio redirigir transmisiones para enviar navegadores infectados a sitios de malware y phishing. Dos muestras de malware vinculadas a los sitios de complementos fueron:

  

ARCADEYUMGAMES.exe, que lee las claves relacionadas con el servicio de terminal y accede a información potencialmente confidencial de los navegadores locales, y

MapsTrek.exe, que tiene la capacidad de abrir el portapapeles

Todos los sitios menos uno utilizados en el esquema no fueron previamente clasificados como maliciosos o fraudulentos por los servicios de inteligencia de amenazas. La excepción fue el estado de Missouri, que enumeró DTSINCE \[.\] Com, uno de los pocos servidores de control codificados, como sitio de phishing.

  

Los investigadores encontraron evidencia de que la campaña ha estado operando desde al menos enero de 2019 y creció rápidamente, particularmente de marzo a junio. Es posible que los operadores estuvieran activos durante un período mucho más largo, posiblemente ya en 2017.

  

Si bien cada uno de los 500 complementos parecía ser diferente, todos contenían un código fuente casi idéntico, con la excepción de los nombres de las funciones, que eran únicos. Kaya descubrió los complementos maliciosos con la ayuda de CRXcavator, una herramienta para evaluar la seguridad de las extensiones de Chrome. Fue desarrollado por Duo Security y se puso a disposición gratuitamente el año pasado. Casi ninguno de los complementos tiene calificaciones de usuarios, un rasgo que dejó a los investigadores inseguros de cómo se instalaron las extensiones. Google agradeció a los investigadores por informar sus hallazgos.

  

**Cuidado con las extensiones**

  

Este último descubrimiento se produce siete meses después de que un investigador independiente diferente documentara extensiones de navegador que levantaron los historiales de navegación de más de 4 millones de máquinas infectadas. Si bien la gran mayoría de las instalaciones afectaron a los usuarios de Chrome, algunos usuarios de Firefox también fueron barridos. Nacho Analytics, la compañía que agregó los datos y los vendió abiertamente, cerró después de la cobertura de Ars de la operación. El informe del jueves tiene una lista de 71 extensiones maliciosas, junto con sus dominios asociados. Tras una larga práctica, Google no identificó ninguna de las extensiones o dominios que encontró en su propia investigación. Las computadoras que tenían uno de los complementos recibieron una notificación emergente que decía que se había "deshabilitado automáticamente". Las personas que siguieron un enlace recibieron una advertencia roja que decía: "Esta extensión contiene malware".

  

El descubrimiento de extensiones de navegador más maliciosas y fraudulentas es un recordatorio de que las personas deben tener cuidado al instalar estas herramientas y usarlas solo cuando brinden un beneficio real. Siempre es una buena idea leer las reseñas de los usuarios para buscar informes de comportamiento sospechoso. Las personas deben verificar periódicamente las extensiones que no reconocen o no han utilizado recientemente y eliminarlas.

  
  

Fuente: [https://www.wired.com/](https://www.wired.com/story/over-500-chrome-extensions-secretly-uploaded-private-data/)

No olvides Compartir... 

  
  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)