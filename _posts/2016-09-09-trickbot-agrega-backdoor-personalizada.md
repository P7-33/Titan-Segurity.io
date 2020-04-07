---
title: 'TrickBot agrega backdoor personalizada y sigilosa a su arsenal'
date: 2020-01-09T14:31:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-2r_LFSWp9Gs/XhcrF2dWFZI/AAAAAAAALl4/99vLBRju3swpuQ6M728uK0tzsgIVPtUwgCLcBGAsYHQ/s640/Malware-Generic.jpg)](https://1.bp.blogspot.com/-2r_LFSWp9Gs/XhcrF2dWFZI/AAAAAAAALl4/99vLBRju3swpuQ6M728uK0tzsgIVPtUwgCLcBGAsYHQ/s1600/Malware-Generic.jpg)

  

Los ciberdelincuentes de habla rusa detrás del malware TrickBot han desarrollado una Backdoor sigilosa llamada "PowerTrick" para infiltrarse en objetivos de alto valor.

  

Según una investigación de SentinelLabs, publicada el jueves, PowerTrick está diseñado para ejecutar comandos y devolver los resultados en formato Base64. Se implementa como un módulo después de que la infección inicial de TrickBot ya se haya instalado en una computadora víctima.

  

"El objetivo final de la Backdoor PowerTrick y su enfoque es evitar las restricciones y los controles de seguridad para adaptarse a la nueva era de los controles de seguridad y explotar las redes de alto valor más protegidas y seguras", según el análisis.

  

Los investigadores de la empresa observaron que primero se implementaba un script de Backdoor inicial más pequeño, a veces en forma de una tarea de PowerShell, que establece contacto con el servidor de comando y control (C2). Después de eso, los operadores de malware envían el primer comando, que es descargar la Backdoor principal PowerTrick.

  

Una vez instalado, PowerTrick realiza las funciones habituales de Backdoor, según el análisis: realiza un registro inicial y luego se encuentra en una solicitud de bucle esperando que se reciban los siguientes comandos. Los ejecuta y devuelve resultados o errores; y puede dormir por ciertas cantidades de tiempo a pedido.

  

Los operadores utilizan TrickBot para llevar a cabo otras tareas, principalmente mediante el aprovechamiento de los servicios públicos de PowerShell. Por ejemplo, SentinelLabs observó que PowerTrick descargaba "letmein", un script basado en PowerShell para conectarse al marco de explotación de código abierto Metasploit, para realizar el reconocimiento e identificar otras máquinas para expandir lateralmente la infestación de TrickBot.

  

"Una vez que el sistema y la red han sido perfilados, los actores limpian sigilosamente y se mueven a un objetivo diferente de elección, o realizan un movimiento lateral dentro del entorno a sistemas de alto valor como las puertas de enlace financieras", anotaron los investigadores.

  

Además de Metasploit, la Backdoor también llama a otros fragmentos de código, que funcionan como Backdoor también. Estos incluyen la variante DNS personalizada del Proyecto Anchor de TrickBot; y el malware de Backdoor More\_eggs JScript (también conocido como Terra Loader o SpicyOmelette), que se vende en Dark Web como una oferta de malware como servicio (MaaS). Además, se ha visto a los cibercriminales utilizando la ejecución directa de código de shell a través de PowerTrick como una metodología adicional para la implementación de la payload.

  

Según SentinelLabs, usar la Backdoor como una puerta de entrada a más Backdoor es un esfuerzo para mantenerse sigiloso.

  

"Esto es algo que hemos observado con frecuencia donde los actores modificarán o crearán nuevos sistemas de entrega con frecuencia para evitar restricciones y controles de seguridad", dijeron los investigadores.

  

TrickBot se desarrolló en 2016 como un malware bancario para suceder al troyano bancario Dyre; pero desde entonces, se ha convertido en una de uso múltiple, solución basada en software de actividades ilegales módulo dirigido específicamente a las corporaciones. Si el pasado es un prólogo, la incorporación de PowerTrick a su arsenal es normal en términos del desarrollo continuo y rápido del malware. Más recientemente, ha agregado la capacidad de obtener credenciales de aplicaciones de escritorio y realizar una inyección sigilosa de código; y, se ha visto a sus operadores colaborando con APT Lazarus, vinculada a Corea del Norte.

  

"TrickBot ha cambiado su enfoque a los entornos empresariales a lo largo de los años para incorporar muchas técnicas desde la creación de perfiles de red, la recopilación masiva de datos, la incorporación de exploits transversales laterales", según el análisis de SentinelLab. "Este cambio de enfoque también prevalece en su incorporación de malware y técnicas en sus entregas terciarias que se dirigen a entornos empresariales, es similar a una compañía donde el enfoque cambiará dependiendo de lo que genere los mejores ingresos".

  

  
  

Fuente: [https://threatpost.com/](https://threatpost.com/trickbot-custom-stealthy-backdoor/151663/)

No olvides Compartir... 

  

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)