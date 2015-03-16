# Ejercicios de teoría del tema 2.
### Juan Francisco Robles Fuentes

## Ejercicio T2.1:
**Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema)**
Partimos de un sistema formado por Web, Applications, Database, DNS, Firewall, Switch, un Data Center e ISP con las siguientes disponibilidades: 
* Web: 85%
* Applications: 90%
* Database: 99.9%
* DNS: 98%
* Firewall: 85%
* Switch: 99%
* Data Center: 99.99%
* ISP: 95%

Utilizando la fórmula **"As = Ac1 + (1-Ac1) * Ac2"** que mide el porcentaje de mejora en la disponibilidad que se alcanza al replicar un elemento y **"As = Ac1 * Ac2 * Ac3 * ... * Acn"** que mide la disponibilidad final de sistema con respecto a los compoentes que la forman tenemos la siguiente disponibilidad al replicar por primera vez cada elemento: 
* Web: 0.85 + (1-0.85) * 0.85 = **0.9775**
* Applications: 0.9 + (1-0.9) * 0.9 = **0.99**
* Database: 0.999 + (1-0.999) * 0.999 = **0.999999**
* DNS: 0.98 + (1-0.98) * 0.98 = **0.9996**
* Firewall: **0.9775** (La misma que el componente Web).
* Switch: 0.99 + (1-0.99) * 0.99 = **0.9999**
* Data Center: 0.9999 + (1-0.9999) * 0.9999 = **0.99999999**
* ISP: 0.95 + (1-0.95) * 0.95 = **0.9975**

Replicando cada elemento una sola vez se obtiene la siguiente disponibilidad: 
(0.9775*0.99*0.999999*0.9996*0.9775*0.9999*0.99999999*0.9975)*100 = ***94.3%**

Si añadimos otra réplica tendremos: 
* Web: 0.0.9775 + (1-0.9775) * 0.85 = **0.996625**
* Applications: 0.99 + (1-0.99) * 0.9 = **0.999**
* Database: 0.999999 + (1-0.999999) * 0.999 = **0.999999999**
* DNS: 0.9996 + (1-0.9996) * 0.98 = **0.999992**
* Firewall: **0.996625** (La misma que el componente Web).
* Switch: 0.9999 + (1-0.9999) * 0.99 = **0.999999**
* Data Center: 0.99999999 + (1-0.99999999) * 0.9999 = **0.999999999999**
* ISP: 0.9975 + (1-0.9975) * 0.95 = **0.999875**

Al final tenemos una disponibilidad del: **99.213%**

## Ejercicio T2.2:
**Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad.**
Buscando en la web he encontrado las siguientes librerías para el desarrollo de aplicaciones de alta disponibilidad: 
* JBoss: Librería de alta disponibilidad para Java.
* Corosync+Pacemaker: Herramientas para el manejo de clusters.
* Juno OS: Librería de alta disponibilidad para comunicaciones basadas en intercambio de paquetes.
* Nagios XI: librería incluída en Nagios para implementar rutinas de alta disponibilidad.
* Spectra T-Finity: librería de para redundancia y alta disponibilidad.
* HA-OSCAR, The High Availability Linux Project y LikfeKeeper: Herramientas para alta disponibilidad en GNU/Linux.
* DRBD, rsync o Integration: Herramientas para alta disponibilidad de datos.
* UltraMonkey, Linux Virtual Server: Frameworks para alta disponibilidad en GNU/Linux.

## Ejercicio T2.3:
**¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor?**
En la web existe información sobre muchas herramientas de carga como: 
* LoadRunner: Software propietario de HP para medir carga en servidores.
* ApacheBench: Herramienta creada por la fundación Apache para realizar pruebas de carga.
* Siege: Creada por JoeDog Software.
* HeavyLoad: Software libre para realizar pruebas de carga a servidores web.
**10 herramientas gratuitas aquí:** http://www.devcurry.com/2010/07/10-free-tools-to-loadstress-test-your.html

## Ejercicio T2.4:
**En este ejercicio debemos buscar diferentes tipos de productos: 
* (1) Buscar ejemplos de balanceadores software y hardware (productos comerciales).
* (2) Buscar productos comerciales para servidores de aplicaciones. 
* (3) Buscar productos comerciales para servidores de almacenamiento.**

** Apartado 1: **
Ejemplos de balanceadores Software y Hardware comerciales son: 
* Software: Kemp, HAProxy, LVS (Linux Virtual Server), Nginx, Pound, Pen, Zen Load Balancer. 
* Hardware: CISCO, F5 BIG-IP LTM, Radware AppDirector, Ondemand Switch, Coyote Point, Barracuda, etc.

**Apartado 2: **
Ejemplos de servidores de aplicaciones comerciales son: 
GlassFish, Java EE, Microsoft .Net, BEA WebLogic, IBM WebSphere, Sun-Netscape IPlanet, Sun One, Orace IAS, HP Bluestone, Base4 Server o Zope (Código abierto).

**Apartado 3: **
Ejemplos de productos comerciales para servidores de almacenamiento: 
HP ProLiant, Amazon EC2, Windows Azure, Dell PowerEdge, Lenovo ThinkServer, FlyTech, etc.
