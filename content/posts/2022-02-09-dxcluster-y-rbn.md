---
title: "DXCluster y RBN"
date: 2022-02-09
slug: "dxcluster-y-rbn"
categories:
  - "Artículos"
tags:
  - "DXCluster"
  - "DXSpider"
  - "RBN"
  - "Reverse Beacon"
  - "Telnet"
---

Ya hemos comentado en un post anterior algunos [tips sobre las conexiones al «DXCluster»](https://www.eb1tr.com/tips-dxcluster/), hoy iremos un paso mas allá.

#### Concepto de RBN

El concepto de RBN (Reverse Beacon Network) parte como una iniciativa de lograr un flujo de información que se útil en las estaciones de concursos. Inicialmente se trataba de que, en los momentos que una estación en una banda no estaba en TX, un receptor SDR asociado a esa banda realizara una demodulación y decodificación de las transmisiones que se oían. Una red de escucha 24×7 dando información de todo lo que decodifica, GENIAL.

Se trata de un acercamiento a la información mas útil de la que podemos disponer ya que nos aseguramos que las estaciones que ahí se demodulan son recibidas -por ende «trabajables»- por dicha estación.

#### Historia

Con el tiempo la idea se popularizó y, posteriormente, surgió la idea de tener un «agregador» de esta información. Una especie de red «paralela», accesible también por lo protocolos habituales (HTTP y TELNET).

#### Que nos ofrece

Evidentemente una idea de las localizaciones donde una señal ha sido recibida y su SNR en esa estación receptora.

#### Modos

Los modos disponibles en la red RBN son aquellos que sean susceptibles de ser decodificados, básicamente hablamos de CW, PSK, RTTY y FT8/4.

#### Utilidad

La utilidad es evidente. Se trata de una gran fuente de información ya que no depende de que «alguien» oiga una señal como para que un SPOT sea emitido. Esto es particularmente interesante en bandas donde las aperturas dan sorpresas.

#### Como usar la información

##### Conexión a la RED RBN

Podemos hacer una conexion TELNET a la RED RBN para utilizar la información, para ello es necesario saber que los modos se distribuyen por dos conexiones separadas:

RBN CW, conectando a:
    
    
    telnet.reversebeacon.net:7000

RBN MGM, conectando a:
    
    
    telnet.reversebeacon.net:7001

Hay que decir que el volumen de datos es «ingente», daros una idea que en un «Llamado CQ» , dependiendo de las condiciones y banda, es probable que «envíen un SPOT» muchos reversebeacons diferentes con lo que os podéis imaginar si lo multiplicamos por el número de estaciones que hay en el aire y las diferentes bandas y modos. Es información que hay que trabajar de alguna forma.

##### Web de la ReverseBeaconNetwork

La propia red tiene la información almacenada en bases de datos y algunas herramientas de análisis y comparación, es súper interesante y la información que podemos extraer de esos análisis puede ir desde comparar rendimiento de antenas a comparativas con otras estaciones de nuestro entorno o interés.

![](https://www.eb1tr.com/wp-content/uploads/2022/02/rbn-web.png)

Enlace: <http://www.reversebeacon.net>

##### DXSpider, información condensada

Esta red, salvo en algún caso concreto, no estaba disponible para utilizar en la misma conexión los SPOTS «humanos» y los RBN.

No hace mucho tiempo el creador de DXSpider (software que corre gran parte de los nodos que componen lo que conocemos como «DXCluster») ha integrado el envío de la información directamente activando esta característica desde el propio nodo:
    
    
    set/skimmer

Como hemos comentado un poco mas arriba, sin embargo, esta opción nos activa los RBN en TODOS los modos. Podemos hacer una activación algo mas «granular» con el comando:
    
    
    set/skimmer cw ft8

Los modos disponibles son: CW, PSK, FSK, FT8, FT4 y MSK

El funcionamiento con esta información, aunque está documentada, puede ir cambiando, por lo que es necesario -importante, diría- que nos mantengamos en conocimiento de la evolución del desarrollo.

**Los filtros que tenemos aplicados a los SPOTS en general AFECTAN TAMBIEN a los SPOTS RBN**. Además de esto podemos hacer reglas concretas para los RBN, pero siempre sabiendo que si tenemos hechas restricciones a nivel general éstas afectarán a los RBN.

![](https://www.eb1tr.com/wp-content/uploads/2022/02/rbn.png)

Como se puede ver en la captura el formato en el que la red de DXSpider envía la información RBN es bastante particular, se hace una tratamiento de la información en 3 aspectos:

  1. Condensación: Se concentra la información de múltiples SPOTS RBN en UN SOLO SPOT (esto quita mucho «ruido»).
  2. Enriquecimiento: Se añaden los campos -no originales- Q y Z. 
     * Q, «calidad»: 
       * El número que lo acompaña es la cantidad de diferentes RBN que lo han reportado.
       * El «*» significa que, entre los spots, ha podido haber un poco de desplazamiento de frecuencia entre ellos.
       * El «+» significa que es una estación que ya ha sido reportada alli, lleva «algún tiempo» en el aire.
     * Z, zonas CQ: 
       * Los números en este campo indican que zonas CQ han emitido un SPOT de esa estación (que fueron condensados), aparte de la que realmente se emite como origen del SPOT (la de la estación SPOTTER).
  3. Cadencia: Se impide que una misma estación se vuelva a repetir hasta que no pasa un tiempo «prudencial» del SPOT anterior.



##### SEEME

El funcionamiento descrito, a mi punto de vista, tenía un problema. Al estar condensanda la información de TODOS los SPOTS RBN en uno (idealmente) perdíamos la posibilidad de tener la información de quienes, exactamente, nos estaban escuchando (a nosotros). Esto es lo que vino a resolver el SEEME.

Se activa con el siguiente comando:
    
    
    set/seeme

La información que obetenemos es esta:

![](https://www.eb1tr.com/wp-content/uploads/2022/02/seeme.png)

Estos SPOTS, que tienen como origen la red RBN, entran directamente y saltandose cualquier filtro. Los recibiremos conjuntamente con el resto de información (SPOTS «humanos» + SPOTS RBN «concentrados»).

#### Conclusión

Tenemos, como nunca, una cantidad de información realmente de calidad y con un nivel de personalización que permite no «morir enterrado en ella». Es importante que conozcamos estos pequeños «hacks» para extraer toda la información que nos pueda ser de utilidad.

**Los nodos que dispone la URE** para que podáis acceder al DXCluster, ya sea a mano o para vuestros «libros de guardia» o «logs de contest», **tienen estas opciones disponibles** y con una calidad en las fuentes de información que **son de las mejores en la red** , sin lugar a dudas.

**Podéis hacer vuestra conexión TELNET a los nodos de URE a la dirección ea4ure.com por el puerto 7300.**
