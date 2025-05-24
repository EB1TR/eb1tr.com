---
title: "WeeWX"
date: 2017-09-13
slug: "raspberry-weewx"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "Meterologia"
  - "RaspBerry Pi"
  - "Watson W-8681"
  - "WeeWX"
---

#### Un poco de historia

Desde hace ya una temporada dispongo en la estación de radio de una estación meteorológica, se trata de una Watson W-8681 que en su día me encapriché en tener y la verdad es que el cacharro dificilmente pueda estar mejor en relacion calidad/funcionalidad/precio.

En un primer momento ha estado funcionando con el software original, ni me acuerdo ya de el, ya que [Cumulus ](http://sandaysoft.com/products/cumulus)es el estandar (al menos bajo Windows) en estaciones de este tipo, en plan aficionado. Cumulus esta MUY bien, cuenta con muchas opciones entre las que destaco la integración en el envío de datos hacia Wunderground, PWS Weather, Twitter y la red de APRS. durante una buena temporada he estado funcionando esa configuración aunque apagar el ordenador de la estación de radio generaba (evidente) una interrupcion de los datos que se envian. ¿El resultado? muchos días de desconexion, demasiado engorroso tener que utilizar el ordenador de la estación de radio.

Investigando un poco di con la solución, una mezcla casi perfecta entre hardware y software. El hardware: una RaspBerry Pi. El software: [WeeWX](http://www.weewx.com/).

![](https://www.eb1tr.info/wp-content/uploads/2017/09/687474703a2f2f77656577782e636f6d2f77656577782d6c6f676f2d343537783433372e706e67-e1505296946335.png)

Hacerlo funcionar ha sido muy fácil, no se requiere casi ningún conocimiento en GNU/Linux (sistema operativo de la RaspBerry Pi). Lo importante es ir configurando los distintos servicios OnLine para equiparar las funcionalidades con los programas tradicionales. Equiparar estas funcionalidades, y superarlas, no ha sido ya tan fácil, ha habido que tener un poco de imaginación; a día de hoy los datos de la estación meteorológica salen a estos servicios:

  * Web propia
  * Twitter
  * Facebook
  * Weather Underground
  * APRS
  * PWS Weather
  * Weather Cloud
  * MeteoRadio
  * Pocket PWS (Android)



Las funcionalidades mas básicas se obtienen fácilmente, os propongo una guía ultra sencilla de como llegar a los primeros resultados.

#### Glosario de Comandos:

**sudo:** SUper user DO, hacer como «Super User» una tarea nos da permisos en el sistema. Necesario para muchas de las tareas de configuración.

**nano:** Editor de texto que utilizaremos para la edicion de ficheros. Guardamos con «Control+O» y salimos con «Control+X»

**tail:** Programa que nos permite ver la últimas líneas de un archivo de texto.

**apt-get:** Comando que sirve para gestión de paquetes en repositorios, instalarlos, desinstalarlos, etc.

**repositorio:** «Lugar» donde se encuentra el software disponible para nuestro sistema.

**wget:** Descargar un fichero desde internet.

**dpkg:** Instalar un fichero desde un paquete local, no en repositorio

#### Conectar a la terminal de la RaspBerry y actualizar

Quemamos la imagen de RaspBian Lite (sin entorno gráfico) segun [las intrucciones.](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

Pinchamos la SD en la RaspBerry Pi

Nos conectamos por SSH desde un terminal (ordenadores Linux/Mac) o mediante Putty (Windows), por ejemplo; para ello deberemos conocer la IP que tiene la RaspBerry Pi, y que en este ejemplo supondremos como 192.168.1.100:

> ssh pi@192.16.1.100

login: pi  
password: raspberry

Actualizamos el sistema

> sudo apt-get update  
>  sudo apt-get upgrade

#### Instalación de WeeWX

En un navegador copiamos el link de descarga de WeeWX y, ya en la terminal de la Raspi nuevamente, lo descargamos:

> wget http://www.weewx.com/downloads/weewx_3.7.1-1_all.deb

Instalamos WeeWX:

> sudo dpkg -i /home/pi/weewx_3.7.1-1_all.deb

Seguimos el procedimiento que nos dicta el instalador prestando especial atencion a las unidades y la sintaxis que nos propone.

En la instalacion de WeeWX quedan varios paquetes marcados para instalar de los que depende su funcionamiento, los instalamos:

> sudo apt-get -f install

Instalamos otros paquetes necesarios:

> sudo apt-get install python-dev python-pip
> 
> sudo pip install pyephem (este último tarda un poco)

Detenemos el demonio WeeWX:

> sudo /etc/init.d/weewx stop

Durante el proceso de instalación el mismo programa nos irá pidiendo datos del modelo de estación meteorológica, nombre, ubicacion (nombre y latitud/longitud en grados decimales), altura, etc. Es recomendable tener estos datos a mano para no necesitar detener el proceso, de todas formas todo ello se puede editar desde la configuración de WeeWX.

Editamos la configuracion de WeeWX:

sudo nano /etc/weewx/weewx.conf

#### La Meteo en APRS

Modificamos los parámetros de los servicios a los que queremos subir datos. Recordar que tenemos que tener una cuenta en cada uno de ellos y que para subir datos a APRS (CWOP) debemos colocar EA1XXX-13 como indicativo y «Passcode» que obetenemos del registro en: <http://www.apritch.myby.co.uk>/uiv32_uiview32.php?lang=english  
Los servicios que no queremos habilitar los anulamos con el parametro «enable = false», como se puede ver en la mayoria de ellos.

**¡¡¡ATENCION!!!**  
Dado que el usuario y constraseñas de RaspBerry son genéricos se recomienda el cambio de contraseña. Para ellos podemos utilizar el siguiente comando:

> sudo passwd

Cuando instalamos el RaspBian en la SD el tamaño de la partición queda determinado por el de la imagen que se generó en su día. Puede que este espacio (seguramente) sea sensiblemente menor al que tenemos disponible en la tarjeta SD, para ampliar la particion, así como para tocar otra serie de parametros en la configuracion de RaspBian tenemos un programa que inicializamos:

> sudo raspi-config

Esta se trata de la instalación mas básica, espero os sirva de guía y no dudéis en contactar si necesitáis un poco de ayuda adicional.
