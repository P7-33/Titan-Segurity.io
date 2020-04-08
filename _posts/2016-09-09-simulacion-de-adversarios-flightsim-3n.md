---
title: 'Simulación de adversarios... FlightSIM 3/n'
date: 2019-10-02T18:31:00+01:00
draft: false
---

Estimados amigos de Inseguros !!!  
  
En este tercer episodio de la simulación de adversarios, voy a comentar la herramienta [FlightSim](https://github.com/alphasoc/flightsim), que no es un simulador de vuelo... es una herramienta de generación de "ruido" esta vez de tráfico de red para comprobar nuestras capacidades de detección.  
  

[![](https://1.bp.blogspot.com/-1nUatass1mU/XZI8sMigDmI/AAAAAAAAGYY/L-FYri9o07EDuUXKVNCokyeW-MZrl2hpQCLcBGAsYHQ/s640/41nsIGIBVXL._QL40_SX400_.jpg)](https://1.bp.blogspot.com/-1nUatass1mU/XZI8sMigDmI/AAAAAAAAGYY/L-FYri9o07EDuUXKVNCokyeW-MZrl2hpQCLcBGAsYHQ/s1600/41nsIGIBVXL._QL40_SX400_.jpg)

  
Como vimos con [Caldera](https://kinomakino.blogspot.com/2019/09/caldera-simulacion-de-adversarios-golpe.html), [Infection Monkey](http://kinomakino.blogspot.com/2017/01/infection-monkey-suelta-el-mono-y-ver.html) hace unos años o recientemente [Uber Metta](https://kinomakino.blogspot.com/2019/09/uber-mettasimulacion-de-adversarios-2n.html), Flightsim genera distintos tipos de eventos, bueno eventos no, genera las actuaciones que deben generar eventos en nuestros sistemas. Algunos de los módulos que tienen, y que por el nombre describen muy bien el trabajo que hacen son:  
  

Module

Description

`c2`

Generates a list of C2 destinations and generates DNS and IP traffic to each

`dga`

Simulates DGA traffic using random labels and top-level domains

`scan`

Performs a port scan to random RFC 5737 addresses using common ports

`sink`

Connects to random sinkholed destinations run by security providers

`spambot`

Resolves and connects to random Internet SMTP servers to simulate a spam bot

`tunnel`

Generates DNS tunneling requests to \*.sandbox.alphasoc.xyz

  
La instalación es muy sencilla, podemos hacerlo por github o usando las comodidades de GO.  
  
Los comandos son muy sencillos y podemos usar la opción -dry para que genere los datos sin realizar el tráfico de red. No vayas a probarlo sin avisar y le des el fin de semana al SOC.  
  
Yo por si acaso activo las capturas de red a ver que hace el simulador...  
  

[![](https://1.bp.blogspot.com/-DFnIxYaOAZg/XZJBHWKnZQI/AAAAAAAAGYo/-0rxOC-oGLUWxjwy7gXyZsS7DC3bH3Y-ACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.36.46.png)](https://1.bp.blogspot.com/-DFnIxYaOAZg/XZJBHWKnZQI/AAAAAAAAGYo/-0rxOC-oGLUWxjwy7gXyZsS7DC3bH3Y-ACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.36.46.png)

  

[![](https://1.bp.blogspot.com/-P5mgVJnaJp0/XZJBHUoakEI/AAAAAAAAGYs/EoLW2TvFzcIfpyPViclyO9_Ws4xLciPZACLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.46.06.png)](https://1.bp.blogspot.com/-P5mgVJnaJp0/XZJBHUoakEI/AAAAAAAAGYs/EoLW2TvFzcIfpyPViclyO9_Ws4xLciPZACLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.46.06.png)

  

[![](https://1.bp.blogspot.com/-33gZB7WxAJI/XZJBHeUw5oI/AAAAAAAAGYk/xBRzF_bsY7Uwx3DqlaiqcsgsCS-b6U45QCLcBGAsYHQ/s640/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.50.43.png)](https://1.bp.blogspot.com/-33gZB7WxAJI/XZJBHeUw5oI/AAAAAAAAGYk/xBRzF_bsY7Uwx3DqlaiqcsgsCS-b6U45QCLcBGAsYHQ/s1600/Captura%2Bde%2Bpantalla%2B2019-09-30%2Ba%2Blas%2B19.50.43.png)

  
Una herramienta muy sencilla. Por poco que puedas leer el lenguaje GO y puedas ver los módulos, podrás adoptar la ejecución a los parámetros que te interesen.  
  
Por cierto, échale un vistazo al código, porque para algunas cosas se va contra la API de los programadores... y lo mismo estamos siendo hackeados nosotros.  
  
Espero que te guste y lo uses !!!