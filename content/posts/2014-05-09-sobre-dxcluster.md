---
title: "A vueltas con la Configuración de los DXCluster"
date: 2014-05-09
slug: "sobre-dxcluster"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "CCCluster"
  - "Contest"
  - "DXCluster"
  - "Spot"
  - "Telnet"
  - "VE7CC"
---

No descubro absolutamente nada si afirmo que la conexión de redes de anuncio de estaciones (DXCluster) son «el pan de cada día», tanto en DX como para concursos, hoy hablamos de configuración de DXCluster.

Lo perfiles de DX y Concursos pueden ser bastante distintos a la hora de configurar un cliente para conectarnos y hacer un filtrado que permita no tener un exceso de información que nos convierta los avisos en ingobernables. Desde hace tiempo, aprovechando que los DXCluster guardan un _«perfil»_ por cada SSID que se conecta es que utilizo VE7CC Cluster para hacer estas configuraciones, los resultados han sido estupendos, podemos filtrar bandas por horarios, origen de los avisos, banda de los mismos, segmentos, modos, etc., etc. Una solución, prácticamente, para cada usuario.

[![ve7cc-screenshot](http://www.eb1tr.info/wp-content/uploads/2014/05/ve7cc-screenshot-1024x819.jpg)](http://www.eb1tr.info/wp-content/uploads/2014/05/ve7cc-screenshot.jpg)

Captura del Software Cliente de VE7CC, el CC Cluster.

Uno de los puntos que quedaba por resolver era lo que pasaba con Spots que no saliesen en el Host al que nos conectábamos, me explico: Debido a la ingente cantidad de mensajes que provienen de EA (cosa que no entraré a valorar) es sabido que hay ciertos DXCluster que tienen _«capado»_ los avisos desde EA, entre otras cosas, por no tener que _«fumarse»_ Spots de Vértices, Hermitas, DME´s, monumentos, puentes y demás. el tema es: ¿que pasa si nos conectamos a uno de estos DXCluster? Pues es probable que nos perdamos parte de la información que corre por la red, este es uno de los motivos, hay mas… muchas veces ciertos Spots se pierden de unas redes a otras y aparecen en VE7CC y no en K1TTT, o al revés.

[![cnexiones-salientes](http://www.eb1tr.info/wp-content/uploads/2014/05/cnexiones-salientes.jpg)](http://www.eb1tr.info/wp-content/uploads/2014/05/cnexiones-salientes.jpg)

Listado de conexiones salientes.

Pues bien, VE7CC ha añadido en su software cliente la **posibilidad de redundar la información de hasta 6 Hosts distintos** , una posibilidad importantísima. Esto se podía hacer ya, pero era un poco mas complejo para un nivel de usuario final, requería algo de experiencia a nivel de configuración de un Host y hacia la implementación mas engorrosa.

Otra de las MUY **interesantes opciones del programa es la posibilidad de funcionar como Host** , esto nos permite que cualquier programa que estemos utilizando **en el mismo ordenador, otro en la misma red o a través de Internet pueda utilizar los datos (ya filtrados y unificados) para si mismo** , con lo que tendríamos una capa de conexión y filtrado de Spots separada al software que utilizamos para libro de guardia o Contest (en mi caso Logger32 para lo primero y N1MM para lo segundo). Logger32 viene experimentando parte de esto a través de una segunda ventana de Telnet, aunque esta está mas orientada a la recepción de datos Skimmers.

[![cluster-primario](http://www.eb1tr.info/wp-content/uploads/2014/05/cluster-primario.jpg)](http://www.eb1tr.info/wp-content/uploads/2014/05/cluster-primario.jpg)

Detalle de conexión establecida como «primaria», por donde saldrán los Spots.

**En la Práctica**  
El llevar este concepto a la práctica es muy sencillo. Parto de la base de que todos tenemos nuestro software de control de QSO´s funcionando con un DXCluster (el que sea).

  * Lo primero es instalar la versión 3 de CC Cluster, [según los pasos de esta Web](http://www.bcdxc.org/ve7cc/Ver3/V3Help.htm).
  * Lo segundo es configurar nuestros datos (**Configuration >User Info**).
  * Nos conectamos a un DXCluster (**Configuration >Node (Telnet)**)
  * Se nos abre una ventana y, a partir de ahí, podemos ir agregando conexiones salientes a gusto.
  * Una vez que «vemos pasar información» estamos en condiciones de establecer la posibilidad de usar este cliente, a su vez, como Host (**Configuration >Ports Logging>Telnet>Enable Telnet**).
  * Configuramos nuestro Logger32 (o el que corresponda) para que se conecte a la IP 127.0.0.1 por puerto 7300 y ¡voilá!



Hay que aclarar que cada uno de los filtrados y configuraciones se hacen en cada DXCluster por separado, de tal forma que podemos hacer cosas realmente potentes, como recibir Spots de distintas zonas/bandas por horarios, etc.

Ojalá esta información os sea de utilidad, si así es, podéis dejar vuestra opinión mas abajo, saludos.
