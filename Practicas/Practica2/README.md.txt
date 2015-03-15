Servidores Web de Altas Prestaciones
====================================
3� Grado en Ingenier�a Inform�tica 2014/2015
--------------------------------------------


# PR�CTICA 2: Clonar la informaci�n de un sitio web.
### Juan Francisco Robles Fuentes

Objetivos principales de la pr�ctica:
* Aprender a copiar archivos mediante `ssh`.
* Clonar contenido entre servidores.
* Acceso a m�quinas de forma remota sin contrase�a usando `ssh`.
* Planificar tareas en `cron`.

En primer lugar copiaremos archivos entre servidores usando `ssh`. Copiaremos un directorio siguiendo los siguientes pasos: 
* Comprimimos con `tar` m�s los argumentos `czf -` el directorio.
* Enviamos el directorio comprimido con **�ssh�** al otro servidor como **�tar.tgz�**. 
* Comprobamos que el archivo se ha creado en la segunda m�quina.

![fichero_tar_enviado](Imagenes/fichero_tar_enviado.png)

Para ficheros de m�s peso ser� necesario utilizar `rsync`, un software m�s potente que permite realizar copias controladas entre m�quinas. Para hacer uso de este software podemos usar `rsync` con argumentos `-avz -e` y `ssh root@192.168.116.128:/var/www /var/`. Una vez lanzada la orden, se nos pedir� la contrase�a del usuario **�root�**, acto seguido se mostrar� por pantalla las acciones realizadas. 
Comprobamos que los archivos se han copiado correctamente.

![copia_rsync](Imagenes/copia_rsync.png)

Un aspecto importante de la pr�ctica y de la gesti�n de servidores es el poder acceder entre m�quinas de forma fluida. Para ello tendremos que permitir el acceso entre las m�squinas mediante el uso de claves. 
Los pasos que hay que seguir para cubrir este objetivo son: 
* Generar la clave en el servidor desde el que se quiere realizar la conexi�n usando `ssh-keygen �t dsa`, que nos generar� una clave DSA. 
* Asignar un nombre a la clave (en mi caso no le he dado ninguno y, por tanto, pasa a tener el nombre por defecto ide_dsa e ide_dsa.pub).
* Introducir una contrase�a (ninguna en mi caso).

![generando_dsa](Imagenes/generando_dsa.png)

La clave se almacena en **�/root/.ssh/id_dsa.pub�**. 

* Copiar la clave al servidor al que nos queremos conectar usando `ssh-copy-id �i .ssh/id_da.pub root@192.168.116.128`. Ahora, con `rsync` podemos hacer copias v�a `ssh` sin tener que introducir la contrase�a para el acceso entre servidores. 

![copiando_clave_dsa](Imagenes/copiando_clave_dsa.png)

* Podemos consultar el archivo de claves permitidas en el primer servidor (**/root/.ssh/authorized_keys**), al final de este existe una entrada que indica que est� permitida la conexi�n mediante `ssh` al usuario **�root�** desde el equipo **�alphaTwo�**.

![confirmacion_acceso_dsa](Imagenes/confirmacion_acceso_dsa.png)

Podremos comprobar el funcionamiento de la conexi�n sin clave conect�ndonos mediante `ssh` al servidor principal desde secundario ejecutando cualquier orden como `uname �a`.

![prueba_conexion_dsa](Imagenes/prueba_conexion_dsa.png)

En este momento podemos volver a realizar la copia del directorio **�/var/www/�** con `rsync` pas�ndole nuevos argumentos como `--delete` o `-- exclude` e indicando que nos vamos a conectar como **�root�** (-e `ssh �l root`). Si hemos realizado correctamente la creaci�n y copiado de las claves, `rsync` se ejecutar�a pedirnos que introduzcamos contrase�a.

![rsync_no_clave](Imagenes/rsync_no_clave.png)

Para finalizar con los objetivos, se automatizar� la copia con `rsync` mediante `cron`. Para ello se crea un script que se encargar� de la operaci�n de copiado con `rsync`.

![script_sincron_www](Imagenes/script_sincron_www.png)

Una vez creado el script, le damos permisos de ejecuci�n con (`chmod 744 scriptActualizar.sh`) y lo probamos.

![sincr_www](Imagenes/sincr_www.png)

Para �ltimo, a�adimos una nueva tarea al **�crontab�** con **� nano /etc/crontab�**), para que cada hora se realice la copia de seguridad en nuestra m�quina replicante, deberemos a�adir:

```
0 *      * * *  root    /root/scriptActualizar.sh
```

Con esta l�nea indicamos que en el minuto **�0�** de cada hora, de cada d�a del mes, de cada mes, de cada d�a de la semana, el usuario **�root�** ejecute el script **�/root/scriptActualizar.sh�**, para que realice la copia del contenido actualizado del directorio **�/var/www/�** de la m�quina principal a la m�quina replicante.

![modif_crontab](Imagenes/modif_crontab.png)