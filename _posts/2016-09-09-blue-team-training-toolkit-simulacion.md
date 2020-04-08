---
title: 'Blue Team Training Toolkit... simulación de adversarios'
date: 2019-10-08T12:20:00+01:00
draft: false
---

Estimados amigos de Inseguros!!!  
  
Seguimos poniendo a prueba nuestros sistemas con la simulación de adversarios. Este artículo pertenece a una serie más completa con distintas aproximaciones y ejemplos, así como herramientas y soluciones completas. Puedes leer el artículo de [Caldera](http://kinomakino.blogspot.com/2019/09/caldera-simulacion-de-adversarios-golpe.html), de [Uber](http://kinomakino.blogspot.com/2019/09/uber-mettasimulacion-de-adversarios-2n.html), [Flight Simulator](http://kinomakino.blogspot.com/2019/10/simulacion-de-adversarios-flightsim-3n.html)...  
  
En el turno de hoy, vamos con una herramienta denominada [Blue Team Training Toolkit](https://www.bt3.no/features/), muy descriptivo el nombre.  
  

[![](https://1.bp.blogspot.com/-RXv22PiLPHs/XZuJ8iOqyjI/AAAAAAAAGZY/IvbER1ahMXccRecUEB9MrihwRKBBhd5RgCLcBGAsYHQ/s640/bt3_logo_reg_small.png)](https://1.bp.blogspot.com/-RXv22PiLPHs/XZuJ8iOqyjI/AAAAAAAAGZY/IvbER1ahMXccRecUEB9MrihwRKBBhd5RgCLcBGAsYHQ/s1600/bt3_logo_reg_small.png)

  
  
El software tiene una estructura de menús muy parecida a metasploit, en la que podemos hacer show modules, show options, set valor y cosas así, muy intuitivos.  
  
Tiene 3 funciones claras, simulación de peticiones de malware a C&C, retransmisión de capturas de red y uso de ficheros sospechosos por imitación de MD5. Vamos a ir instalando y usando la aplicación para ver las funciones en detalle.  
  
Una vez solventado algún pequeño problema con el [instalador](https://www.youtube.com/watch?v=VAd2dYLQlwk&list=PLUANA2JtKjNs1Bjwdt86hG215QKsoDorO&index=2) y python tenemos acceso al framework.  
  

[![](https://1.bp.blogspot.com/-ff0RSATzm60/XZuI9_DHk_I/AAAAAAAAGZQ/tqRBwj-ATnAtMm0RjnEl2qtZ6Ap8HKzlgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B20.48.44.png)](https://1.bp.blogspot.com/-ff0RSATzm60/XZuI9_DHk_I/AAAAAAAAGZQ/tqRBwj-ATnAtMm0RjnEl2qtZ6Ap8HKzlgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-07%2Ba%2Blas%2B20.48.44.png)

  
Empezamos como es menester pidiendo ayuda a la aplicación, no al vecino. Un Help nos posiciona correctamente ante el problema.  
  

[![](https://1.bp.blogspot.com/-EvqNaexK-Ns/XZw7zHdT1QI/AAAAAAAAGZk/x-B2YDwOW8E6qXI9eBrbqr62YLl4KAdqQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.33.06.png)](https://1.bp.blogspot.com/-EvqNaexK-Ns/XZw7zHdT1QI/AAAAAAAAGZk/x-B2YDwOW8E6qXI9eBrbqr62YLl4KAdqQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.33.06.png)

  
Voy a optar por la opción de generar un nuevo token con apisignup para la API. El servicio es gratuito, pero tiene distintas opciones de subscripción para comercializar el producto. Voy a optar por registrarme para la versión community, que si bien no es la más completa, si es gratis.  
  
Al más puro estilo Metasploit, voy navegando por los módulos para ver que me ofrece la herramienta. Show Modules está bien.  
  
Para esta primera prueba vamos a usar Maligno, una estructura cliente servidor para emular las conexiones que hace el malware hacia un C2, reproduciendo metadatos conocidos para testear nuestra capacidad de detección, que es de lo que se trata...  
  

[![](https://www.encripto.no/wp-content/uploads/2018/07/Picture1-2.png)](https://www.encripto.no/wp-content/uploads/2018/07/Picture1-2.png)

[![](https://1.bp.blogspot.com/-lA34N4zYOYM/XZw-mpSIrzI/AAAAAAAAGZw/Dd8icYChKCAvqQmLoZUHRowN-XEf-8eFwCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.44.54.png)](https://1.bp.blogspot.com/-lA34N4zYOYM/XZw-mpSIrzI/AAAAAAAAGZw/Dd8icYChKCAvqQmLoZUHRowN-XEf-8eFwCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.44.54.png)

  
  
Seteamos el servidor que hará de C2 con la ip indicada y hacemos un show profiles. Veremos la lista de perfiles de imitación que tenemos disponibles, con la salvedad de que algunos son de pago, 1$ creo recordar que cuestan, pero vamos a elegir uno gratuito, que es gratis xD.  
  

[![](https://1.bp.blogspot.com/-wbCV2FQftW4/XZxARplY9JI/AAAAAAAAGZ8/-EHwJZ1HyZAiJoOkLKEPXFmwLoSSS0s9gCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.52.12.png)](https://1.bp.blogspot.com/-wbCV2FQftW4/XZxARplY9JI/AAAAAAAAGZ8/-EHwJZ1HyZAiJoOkLKEPXFmwLoSSS0s9gCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B9.52.12.png)

  
Hacemos un download nuclear, luego un set profile nuclear y luego hacemos un genclient para generar el cliente que realizará las conexiones contra nuestro Command And Control.  
  
Si nos vamos a la carpeta profiles podremos ver el código en python de la actividad que vamos a recrear relacionada en este caso con nuclear.  
  

[![](https://1.bp.blogspot.com/-AGjZNHX8WtU/XZxCR-625CI/AAAAAAAAGaI/Mftw--f56zUXlW4hboTDlsbs6QFvm2NbwCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B10.00.15.png)](https://1.bp.blogspot.com/-AGjZNHX8WtU/XZxCR-625CI/AAAAAAAAGaI/Mftw--f56zUXlW4hboTDlsbs6QFvm2NbwCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B10.00.15.png)

  
También es interesante ver el fichero que crea cliente.  
  
Ahora es el turno de irnos a nuestra máquina "cliente" y ejecutar el python.  
  
Hemos probado varias simulaciones y hemos puesto un snort en la máquina para ver la detección.  
  

[![](https://1.bp.blogspot.com/-IEdCZkjN3Qw/XZxpsns6aTI/AAAAAAAAGaU/sqo3M3C0ObomPWpHJ7mJ7NjB2YemvpY7ACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.48.10.png)](https://1.bp.blogspot.com/-IEdCZkjN3Qw/XZxpsns6aTI/AAAAAAAAGaU/sqo3M3C0ObomPWpHJ7mJ7NjB2YemvpY7ACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.48.10.png)

  

[![](https://1.bp.blogspot.com/-Ftpt_ywye3E/XZxpsuBhBYI/AAAAAAAAGac/Zyw3qKlIBIU1A-VFeBpHfkvUujRZrAuwgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.48.30.png)](https://1.bp.blogspot.com/-Ftpt_ywye3E/XZxpsuBhBYI/AAAAAAAAGac/Zyw3qKlIBIU1A-VFeBpHfkvUujRZrAuwgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.48.30.png)[![](https://1.bp.blogspot.com/-gJ-AcbjNebs/XZxpsp6VSDI/AAAAAAAAGaY/iz2lKiH99SQ_fq5PP3LqTVqVkBwz5-1zQCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.46.50.png)](https://1.bp.blogspot.com/-gJ-AcbjNebs/XZxpsp6VSDI/AAAAAAAAGaY/iz2lKiH99SQ_fq5PP3LqTVqVkBwz5-1zQCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.46.50.png)

  
Depende del conjunto de reglas que tengas tendrás unas detecciones u otras, pero al final, el concepto es simular la comunicación con el C2.  
  
Vamos a probar otra opción interesante de la herramienta, la posibilidad de gestionar la retransmisión de ficheros pcap, cambiando muy fácilmente las direcciones ip y mac.  
  

[![](https://1.bp.blogspot.com/-nhHZneZkkdM/XZxsp-0bXVI/AAAAAAAAGas/uKeHbpUXYB85tbmMu5z2TWldlb1KTgligCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.58.22.png)](https://1.bp.blogspot.com/-nhHZneZkkdM/XZxsp-0bXVI/AAAAAAAAGas/uKeHbpUXYB85tbmMu5z2TWldlb1KTgligCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B12.58.22.png)

  

[![](https://1.bp.blogspot.com/-djOlDzvZzpA/XZxsuaP6HiI/AAAAAAAAGaw/A0TtLyQ3v0IvaQWrPCokJRB1Q4bsz08-ACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.00.36%2B%25282%2529.png)](https://1.bp.blogspot.com/-djOlDzvZzpA/XZxsuaP6HiI/AAAAAAAAGaw/A0TtLyQ3v0IvaQWrPCokJRB1Q4bsz08-ACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.00.36%2B%25282%2529.png)

  

Y ahora vamos a indicar que 192.168.1.3 se convierta en 172.16.1.3  
  

[![](https://1.bp.blogspot.com/-tJ35tpzughY/XZxuCZCSiEI/AAAAAAAAGbE/IKRt90SUTB4ozyg-S1Oy1p1BcnXvhlyOACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.04.20.png)](https://1.bp.blogspot.com/-tJ35tpzughY/XZxuCZCSiEI/AAAAAAAAGbE/IKRt90SUTB4ozyg-S1Oy1p1BcnXvhlyOACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.04.20.png)

  

[![](https://1.bp.blogspot.com/-eqipBqXhw20/XZxuCaoVjOI/AAAAAAAAGbA/Y8RJzWhjmgQSdFwoDux47V3KXLCuGZ3QACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.06.37%2B%25282%2529.png)](https://1.bp.blogspot.com/-eqipBqXhw20/XZxuCaoVjOI/AAAAAAAAGbA/Y8RJzWhjmgQSdFwoDux47V3KXLCuGZ3QACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.06.37%2B%25282%2529.png)

  
Lo bueno de esta funcionalidad es que podemos usar cualquier pcap que nos apetezca, de los muchos que hay disponibles para su estudio.  
  
Otra de las opciones que implementa esta herramienta es la de usar las colisiones matemáticas del algoritmo MD5 para generar hashes, o mejor dicho, ficheros con el mismo hash que muestra clasificadas como maliciosas, como pueda ser una shell inversa con netcat, mimikatz, etc.  
  

[![](https://1.bp.blogspot.com/-Y0ar-hrcNRo/XZxwQLED_MI/AAAAAAAAGbU/C38kPGQcJJsgbnKv09DX-H4GIgl8UFjYgCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.16.03.png)](https://1.bp.blogspot.com/-Y0ar-hrcNRo/XZxwQLED_MI/AAAAAAAAGbU/C38kPGQcJJsgbnKv09DX-H4GIgl8UFjYgCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-10-08%2Ba%2Blas%2B13.16.03.png)

  
Con este módulo solo podemos bajar el fichero , no tiene ninguna interacción más.  
  
Me parece un framework muy potente y que funciona bien, si bien es un poco más complejo de extender que los demás de la serie, pero cualquier persona con conocimientos de python podrá simular las típicas cabeceras usadas en ataques web y recrear ataques de este tipo.  
  
Espero que os haya gustado y próximamente seguimos con otro capítulo !!!  
  
Gracias por leerme.  
  
En especial, este capítulo se lo dedico a Sergio, para saber si me lee el mamón y me lo dice xD