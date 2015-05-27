# Ejercicios de teoría del tema 5.
### Juan Francisco Robles Fuentes. 


##Ejercicio T5.1: 
**Buscar información sobre cómo calcular el número máximo de conexiones por segundo.**

Para calcular el número de conexiones por segundo de una granja web o de un servidor específico podríamos usar herramientas como Apache Benchmark. Para medir las peticiones con esta herramienta estudiada en clase podríamos aumentar prograsivamente el número de peticiones por segundo mientras no se produjese ningun error en ninguna de las peticiones, momento en el que tendríamos una aproximación del número máximo de peticiones soportadas de forma simultánea. Esta manera de proceder es extensible a la mayoría de los benchmarks para servidores (Apache Jmeter, OpenWebLoad, Httperf, etc).

Si lo que queremos monitorizar es son el número de peticiones que el servidor está soportando actualmente, podemos activar opciones (presentes en determinados programas como Apache Benchmark o httperf) como mod-status. Para usar esta característica podemos usar el siguiente código:

    <Location /server-status>
    SetHandler server-status

    Order Deny,Allow
    Deny from all
    Allow from .website.com
    </Location>

Y, para acceder, usamos http://your.server.name/server-status.

Además del mencionado *mod-status* existen otras utilidades como `apache2ctl, iptstate o netstat`.

##Ejercicio T5.2: Instalar wireshark y observar cómo fluye el tráfico de red en uno de los servidores web mientras se le hacen peticiones HTTP.

##Ejercicio T5.3: 
**Buscar información sobre características, disponibilidad para diversos SO, etc de herramientas para monitorizar las prestaciones de un servidor.**

Algunas de las herramientas más utilizadas en la actualidad para la monitorización de las prestaciones de los servidores: 

*Nagios*. 
Nagios es un sistema de monitorización de redes ampliamente utilizado, de código abierto, que vigila los equipos (hardware) y servicios (software) que se especifiquen, alertando cuando el comportamiento de los mismos no sea el deseado. Entre sus características principales figuran la monitorización de servicios de red (SMTP, POP3, HTTP, SNMP...), la monitorización de los recursos de sistemas hardware (carga del procesador, uso de los discos, memoria, estado de los puertos...), independencia de sistemas operativos, posibilidad de monitorización remota mediante túneles SSL cifrados o SSH, y la posibilidad de programar plugins específicos para nuevos sistemas.

Se trata de un software que proporciona una gran versatilidad para consultar prácticamente cualquier parámetro de interés de un sistema, y genera alertas, que pueden ser recibidas por los responsables correspondientes mediante (entre otros medios) correo electrónico y mensajes SMS, cuando estos parámetros exceden de los márgenes definidos por el administrador de red.
Más información en http://es.wikipedia.org/wiki/Nagios

*Cacti*.
Cacti es una completa solución para la generación de gráficos en red, diseñada para aprovechar el poder de almacenamiento y la funcionalidad para gráficas que poseen las aplicaciones RRDtool. Esta herramienta, desarrollada en PHP, provee un pooler ágil, plantillas de gráficos avanzadas, múltiples métodos para la recopilación de datos, y manejo de usuarios. Tiene una interfaz de usuario fácil de usar, que resulta conveniente para instalaciones del tamaño de una LAN, así como también para redes complejas con cientos de dispositivos.
Más información en http://www.cacti.net/

*Munin*. 
Munin es un programa que permite monitorizar uno o varios equipos. Además, presenta la información a través de un servidor web, está hecho en perl y permite el uso de plugins, lo cual lo hace realmente versátil. También muestra una gran cantidad de información mediante unas gráficas creadas con la librería gráfica RRDtool.
Más información en http://www.n1mh.org/monitorizando-redes-con-munin/

*AWStats*. 
AWStats es una herramienta open source de informes de análisis web, apta para analizar datos de servicios de Internet como un servidor web, streaming, mail y FTP. AWstats analiza los archivos de log del servidor, y basándose en ellos produce informes HTML. Los datos son presentados visualmente en informes de tablas y gráficos de barra. Pueden crearse informes estáticos mediante una interfaz de línea de comando, y se pueden obtener informes on-demand a través de un navegador web, gracias a un programa CGI.

Soporta la mayoría de los formatos de archivos log de servidor web conocidos, entre ellos Apache (formato de log NCSA combinado/XLF/ELF o formato común/CLFt), WebStar, IIS (formato de log del W3C) y muchos otros formatos comunes de Internet.
Más información en http://es.wikipedia.org/wiki/Awstats

*Ganglia*. 
Sistema de monitoreo de computadores de alto rendimiento como clusters. Gracias a sus algoritmos consume bastante poco por nodo y utiliza una alta concurrencia a la hora de obtener toda la información tanto a nivel de servicios como hardware de nuestros servidores.
Más información en http://ganglia.sourceforge.net/

**Enlaces de interés**
* http://www.thegeekstuff.com/2009/09/top-5-best-network-monitoring-tools/
