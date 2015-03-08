Servidores Web de Altas Prestaciones
====================================
3� Grado en Ingenier�a Inform�tica 2014/2015
--------------------------------------------

# PR�CTICA 1: Preparaci�n de las herramientas de pr�cticas.
### Juan Francisco Robles Fuentes

El objetivo de esta pr�ctica es instalar y configurar las m�quinas virtuales que utilizaremos durante el desarrollo de las pr�cticas de la asignatura. 
Las m�quinas estar�n alojadas en VM Player, correr�n Ubuntu Server 12.04.2 LTS y, adem�s, tendr�n instalados y configurados Apache + PHP + MySQL.

### Instalaci�n y configuraci�n de las m�quinas virtuales.
#### Autom�tica. 
La primera opci�n es instalar Ubuntu de forma convencional e instalar Apache + PHP + MySQL durante el proceso de instalaci�n. 
Para ello es necesario seguir los pasos indicados en el gui�n de pr�cticas y marcar la instalaci�n de las herramientas en el paso correspondiente, tal y como se indica en la siguiente imagen:

![inst_herramientas](Imagenes/inst_herramientas.png)

#### Por l�nea de comandos.
La segunda opci�n es instalar las herramientas tras instalar Ubuntu usando el siguiente comando: 
`sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-mysql`
`sudo taksel`.

### Comprobaci�n del funcionamiento de las herramientas.
Comprobamos que se ha instalado correctamente el servidor Apache con el siguiente comando:
`ps aux | grep apache` (Este comando filtra los procesos del sistema y devuelve aquellos que contienen "apache")
El resultado ser�a el siguiente para la primera m�quina: 

![estado_apache_AO](Imagenes/estado_apache_AO.png)
y el siguiente para la segunda: 

![estado_apache_AT](Imagenes/estado_apache_AT.png)

### Apertura de ficheros HTML.
Otra comprobaci�n que necesitamos hacer es si el sistema es capaz de cargar archivos HTML. Para ello, siguiendo el gui�n, creamos un fichero HTML y lo llamamos 
curl: 
`curl http://localhost/archivo.html`
El resultado ser�a similar al que se muestra en la siguiente imagen:

![func_curl](Imagenes/func_curl.png)

### Conexi�n de las m�quinas. 
Ante de nada necesitaremos conocer las direcciones IP de ambos servidores, podemos hacer esto usando `ifconfig`:

![direccion_ip_AT](Imagenes/direccion_ip_AT.png)
![direccion_ip_AO](Imagenes/direccion_ip_AO.png)

Como �ltimo paso, nos conectaremos desde el servidor 1 (alphaOne) mediante SSH al servidor 2 (alphaTwo):
`ssh boss@192.168.116.129`
Podemos navegar por el sistema de archivos para asegurarnos de que estamos en la otra m�quina

![conexion_maquinas](Imagenes/conexion_maquinas.png)