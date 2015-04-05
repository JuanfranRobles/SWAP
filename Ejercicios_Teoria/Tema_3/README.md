# Ejercicios de teoría del tema 2.
### Juan Francisco Robles Fuentes

##Ejercicio T3.1:
**Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.**

Para configurar el tráfico de red de forma manual mediante comandos en Linux podemos seguir el siguiente tutorial en el que se enseña a hacerlo usando **iptables**: http://www.ite.educacion.es/formacion/materiales/85/cd/linux/m6/enrutamiento_en_linux.html

Para Windows puede seguirse este tutorial en el que se usa **route**: http://blog.networkbits.es/?p=32

Entre las herramientas que permiten hacerlo de forma gráfica se encuentran: 
* OpenBGD: http://es.wikipedia.org/wiki/OpenBGPD
* Quagga: http://es.wikipedia.org/wiki/Quagga_(enrutador)
* XORP: http://xorp.org/
* BIRD.
* GNU Zebra.
 
##Ejercicio T3.2:
Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes. 
* **Linux**
Las órdenes que podemos usar son: iptables, ip o tc (linux traffic control).
* **Windows**
La orden más conocida es route.

**Herramientas gráficas**
* Shorewall
* WireShark (más conocido. Versiones tanto para Linux como para Windows) 
* PRTG 
* CocoaPacket Analyzer 
* Acrylic Wifi
