---
title: "Tips para conexiones TELNET al DXCluster"
date: 2021-12-12
slug: "tips-dxcluster"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "DXCluster"
  - "DXSpider"
  - "EA3CV"
  - "EA4URE"
  - "Spot"
  - "Telnet"
  - "WebCluster"
  - "WebClusterURE"
---

Hoy en día todos, o casi, utilizamos redes de información y alerta de actividades y DX. Ya hemos tocado la importancia de las fuentes de información en un [post anterior](https://www.eb1tr.com/sobre-dxcluster/), de hace tiempo.

Son popularmente conocidos los diferentes «WebCluster» que proporcionan información de este tipo y nos ayudan en la tarea diaria de ir «tachando» aquellas entidades o referencias que nos hacen falta para nuestros diplomas favoritos.

![](https://www.eb1tr.com/wp-content/uploads/2021/12/Captura-de-pantalla-2021-12-12-a-las-6.46.59-e1639288093600.png)

El actual WebClusterURE (https://webcluster.ure.es).

Webs como DXFunCluster, DXHeat o el propio [WebClusterURE](https://webcluster.ure.es) aprovechan la misma información que esta «circulando» por una red que tiene muchos años y es de la que los diferentes «logs» se nutren de información.

Hoy vamos a conocer, en esta pequeña lista de «tips», algunas cuestiones que tienen que ver con las conexiones que nuestros «logs» hacen con dicha red y como aprovechar mejor la información.

### TIP 1: ¿Que es eso de TELNET?

No me voy a enrollar demasiado. Digamos, simplificando, que TELNET es un protocolo -viejo, bastante viejo- mediante el cual se establece un «canal de comunicación» por el que fluye la información de DX, los SPOTS.

Os dejo un [enlace a Wikipedia](https://es.wikipedia.org/wiki/Telnet) donde podéis profundizar acerca de este protocolo.

### TIP 2: Hay muchos DXCluster, ¿Que diferencia hay entre ellos?

Efectivamente, hay muchos. Por la propia «topología» que tiene la «red de DXClusters» se trata de algo un poco «caótico». Digamos que no hay una «jerarquía» como tal, por lo que unos DXCluster se conectan con otros y la información va fluyendo entre ellos de manera horizontal. La diferencia que podemos encontrar entre ellos es:

Latencia: Los DXCluster que estén mas «cerca» de nosotros nos proporcionaran una latencia mas baja -mas rapidez-, aunque con las conexiones que tenemos ahora mismo, esto debería ser despreciable, salvo casos extremos.

Filtros: En la propia configuración de un Nodo de DXCluster se pueden realizar filtrados, por lo que si nos conectamos a uno que tenga filtros activos para todo el nodo vamos a observar la «perdida» de información, con respecto a otros.

Fuentes: Hemos dicho anteriormente que la red es horizontal, sin mucha jerarquía. Pues bien, cada nodo «elige» a quien se quiere conectar como «vecino» y de quien / a quien recibirá / dará información. Este no es un dato menor, ya que el protocolo propio de comunicación entre nodos establece un numero maximo de saltos desde que se crea hasta que deja de propagarse, por lo que dependiendo de la «calidad» de los nodos a los que te conectes puede ser el flujo de información mejor o peor.

### TIP 3: ¿En todos los nodos hay la misma información?

Debería, aunque puede que no. En el Tip 2 ya hemos comentado que hay, al menos, dos parámetros que pueden influir en el trafico que recibimos de un nodo:

  * Que tenga filtros aplicados
  * La calidad de las fuentes



### TIP 4: ¿Que son los SSID?

Derivado del «packet radio», y también utilizado en redes como APRS y DMR, se trata de un «identificador» adicional a nuestro indicativo que podemos utilizar -en los nodos de DXCluster- para tener aplicadas diferentes «personalizaciones».

Al conectarnos a un nodo de DXCluster se nos pide el indicativo. Podemos ingresarlo tal como es, EB1TR, por ejemplo. O podemos entrar como EB1TR-2, ¿de que sirve?.

Pues bien, como veremos mas adelante, los nodos de la red de DXCluster tienen la posibilidad de activar o desactivar servicios y funciones, así como filtros y su personalización y esta personalización se aplica al SSID con el que nos hemos conectado.

De esta forma podremos tener una serie de filtros y personalizaciones para cuando nos conectamos como EB1TR-1 en, por ejemplo, Logger32 y otra combinación diferente para EB1TR-2, que es el que podemos utilizar, por ejemplo, en N1MM.

### TIP 5: SPOTS de la RBN

Quizás sea tarea de otro post explicar correctamente que es y como funciona la red RBN, vamos a simplificarlo. La red RBN es una red de nodos que tienen como objetivo compartir en una «subred de DX SPOTS» información automatizada referente a las estaciones que se están decodificando, en tiempo real y de forma absolutamente automatizada, en todo el espectro de radio (o al menos donde hubiese este tipo de receptores instalados).

Como he comentado esos SPOTS circulan en una red SEPARADA, se trata de un volumen absolutamente ingente de datos (del orden de los MILES DE SPOTS por hora) por lo que lo hace absolutamente inservible «al ojo humano».

![](https://www.eb1tr.com/wp-content/uploads/2021/12/Captura-de-pantalla-2021-12-12-a-las-4.19.29.png)

Flujo de SPOTS DX con RBN activados.

### TIP 6: Disponibilidad de los datos RBN

En este sentido, el desarrollador de DXSpider, ha hecho un esfuerzo muy grande para «absorber» ese volumen de datos y, aplicando una serie de reglas, hacer que esos datos PUEDAN ser mostrados en la red normal de DXSpots, conjuntamente con los SPOTS «normales».

La «magia» que hace DXSpider es resumir la información redundante de una misma emisión y enriquecerla para que en un único SPOT podamos tener un «contexto» mayor de cómo y donde se esta recibiendo una señal.

Hay que destacar que NO en todos los nodos tenemos la posibilidad de activar esta información. Cabe destacar en este punto la gestión de los Nodos que la URE tiene funcionando que, al estar en las últimas versiones de DXSpider y un sistema de «alta disponibilidad» (múltiples Nodos en un sistema de balanceo de carga) SI que podemos disfrutar de ellos en los nodos de EA4URE.

Los SPOTS que provienen de la red RBN se ven un poco «diferentes»:

El indicativo del «SPOTTER» aparece con una almoadilla «-#».

En el campo comentario aparecen cosas como:
    
    
    DX de W4AX-#:   1825.4    K3TC    CW 10dB Q:8* Z:5    0332Z
    DX de N6TV-#:   3573.0    K4YT    FT8 5dB Q:2+        0332Z

CW, FT8, RTT, etc. indican el modo

El segundo campo, en dB, indica la intensidad de la señal en ESE receptor (el indicativo que viene como SPOTTER)

Q:n Es la «quality» (calidad), el número de receptores de la red RBN que han decodificado esa señal. El * detras del número indica que diferentes receptores lo han oído, ligeramente, en frecuencias diferentes (unos pocos Hz). El + detrás del número indica que ya ha sido reportado anteriormente.

Z:n,n Indica en que zonas CQ, adicionalmente al SPOTTER, ha sido oída esa señal.

### TIP 7: Activar y desactivar RBN

La forma de activar y desactivar RBN, en las conexiones TELNET, es muy sencilla:

**Activar los RBN en todos los modos posibles.**
    
    
    set/skimmer

**Desactivar todos los RBN.**
    
    
    unset/skimmer

**Activar RBN en CW.**
    
    
    set/skimmer cw

**Activar los RBN en esos modos (podemos personalizarlo).**
    
    
    set/skimmer rtty,ft8,ft4,psk31,psk63

### TIP 8: Filtros

Aunque el flujo de datos que proviene de la conexión de nuestro DXCluster favorito a nuestro programa de log es posible que sea filtrado en el mismo, de tal forma que -en el propio programa de log- puedo»filtrar» que información quiero y que no quiero «ver».

Esto es, creo, un estandar en todos los programas de log. Lo cierto es que, por cómo fluye la información (sin campos delimitados en extención ni tipo), cada vez que nos llega un SPOT el programa «gasta CPU» en saber que país es, que banda, desde que país fue anunciado, etc. etc.

**Vamos a plantear 3 supuestos para ilustrar la necesidad del uso de filtros:**

  * Resulta evidente que si la cadenacia de SPOTS se incrementa, el gasto de CPU aumenta de forma lineal cuando filtramos en nuestro log.
  * Muchas veces podemos vernos en la situacion que tenemos que leer la información «en crudo» según va llegando del nodo, directamente como si de una «consola» se tratase.
  * Podemos vernos, también, en la necesidad de disminuir el tráfico de SPOTS que circula entre el nodo -que es nuestro «servidor»- y nosotros -clientes- por razones tan diversas como: estar en una zona con mala conectividad, hacerlo desde una conexion tarificada, etc.



Para estos supuestos podemos hacer uso de una magnífica herramienta que solventa todo lo anterior de una sola vez, los filtros.

### TIP 9: Ejemplos prácticos de filtros:

La casuística de los filtros puede ser muy compleja, dependiendo de las necesidades. En este sentido os recomiendo leer detenidamente la [información facilitada por Jim/W3BG](http://www.dxcluster.org/main/filtering_en.html) sobre ellos, aunque daremos algunos ejemplos sencillos.

Primero señalaremos que el nodo al que nos conectamos tiene 10 filtros, en cada unos de ellos podemos meter «reglas» para que, en conjunto, den el flujo de información que nosotros esperamos.

Los filtros pueden ser de «aceptar» SPOTS que cumplan con esa regla (acc/spots n regla) o «rechazar» lo que no cumpla con esa regla (rej/spots n regla). Donde n es el número de filtro (del 0 al 9) y la regla puede ser elegida entre los diferentes «campos» que tiene un SPOT, y por el que puede ser filtrado (país origen, país del SPOT, zona CQ de origen, zona CQ del SPOT, banda, modo, etc.)

Rechazar SPOTS que NO estén en 10m
    
    
    rej/spots 1 not on 10m

Rechazar SPOTS que NO provengan de las zonas CQ 3, 4, 5 o 6
    
    
    rej/spots 2 not by_zone 3,4,5,6

El resultado, en este caso es que tendremos SPOTS en 10m con origen en las zonas CQ 3, 4, 5 y 6

![](https://www.eb1tr.com/wp-content/uploads/2021/12/Captura-de-pantalla-2021-12-12-a-las-5.34.27.png)

Captura real del funcionamiento de esta combinación concreta de filtros.

Aceptar SPOTS que estén en 10m
    
    
    acc/spots 1 on 10m

Aceptar SPOTS que provengan de las zonas CQ 3, 4, 5 o 6
    
    
    acc/spots 2 by_zone 3,4,5,6

El resultado es diferente al ejemplo anterior. Pasan SPOTS por una U otra regla, dando lugar al siguiente flujo:

![](https://www.eb1tr.com/wp-content/uploads/2021/12/Captura-de-pantalla-2021-12-12-a-las-5.27.57.png)

Es factible combinar diferentes campos en el mismo filtro, de tal manera que podríamos:

Aceptar SPOTS en 10m Y que vengan de las zonas CQ 3, 4, 5 o 6
    
    
    acc/spots 1 on 10m and by_zone 3,4,5,6

El resultado es el siguiente:

![](https://www.eb1tr.com/wp-content/uploads/2021/12/Captura-de-pantalla-2021-12-12-a-las-6.03.14.png)

Vemos, entonces, que:
    
    
    rej/spots 1 not on 10m
    rej/spots 2 not by_zone 3,4,5,6

Es equivalente a:
    
    
    acc/spots 1 on 10m and by_zone 3,4,5,6

Aunque puede resultar complejo de entender, a priori, leyendo detenidamente la [guía de Jim/W3BG](http://www.dxcluster.org/main/filtering_en.html) sobre el uso de filtros, podremos determinar con mucha precision la información «en crudo» qué vamos a recibir del nodo.

### TIP 10: Ver filtros aplicados y borrarlos

Es muy importante conocer qué nos está llegando, el comando para ver los filtros aplicados es el siguiente:
    
    
    sh/filter

Si queremos borrar un filtro:
    
    
    clear/spots n (siendo n el número de filtro)

Si queremos borrarlos todos:
    
    
    clear/spots all

### Mis Filtros

En mi caso utilizo, como log de diario, Logger32 y, como log de contest, N1MM. Dentro de las ventanas «Telnet» de cada uno de los dos programas es posible configurar unos «comandos» que pueden enviar diferentes comandos al nodo para, por ejemplo, configurar filtros, ver el estado de los mismos, activar/desactivar RBN, etc.

**En Logger32 tengo configurado los siguientes «shortcuts»:(🆕 update: 17/11/2024 🆕)  
**
    
    
    reject/spots 1 (not on hf) or (on 160m) or (freq 7200/7400)
    reject/spots 2 (not by_zone 14,15,20,33)
    reject/spots 2 (not by_zone 14,15)
    reject/spots 2 (not by_zone 14)
    reject/spots 2 (not by_dxcc ea,ea6,ea8,ea9,f,dl,cn,g,on,pa,hb,i,ct,la,sm,oh,oz,lx,ei,gi,gm,gw,c3)
    reject/spots 3 info {FT[8|4](\s)|RTT(\s)|RTTY(\s)}
    reject/spots 4 info {DXF(\s)|BCN(\s)}
    set/seeme
    unset/seeme
    set/skimmer cw
    set/skimmer
    unset/skimmer
    show/filter
    clear/spots all

**En N1MM tengo configurado los siguientes «shortcuts»:(🆕 update: 04/11/2023 🆕)  
**
    
    
    unset/skimmer
    set/skimmer cw
    set/skimmer
    unset/seeme
    set/seeme
    show/filter
    reject/spots 1 (not on 80m,40m,20m,15m,10m) or (freq 7200/7400)
    reject/spots 2 (not by_zone 14,15,20,33) and (not call_zone 14)
    reject/spots 2 (not by_zone 14) and (not call_zone 14)
    reject/spots 3 info {FT[8|4](\s|)|RTT(\s|)|RTTY(\s|)}
    clear/spots all

### Conclusión

  * Es imprescindible conocer como funciona la red de DXCluster, espero haber echado un poco de luz al respecto.
  * Determina la calidad de la información que consumimos el nodo al que nos conectamos, **la URE tiene una de las mejores infraestructuras conectando a _ea4ure.com:7300_** , con RBN disponible, enlaces que garantizan una información excepcional y el soporte de Kin/EA3CV, SySop del sistema.
  * Puede resolver muchas casuisticas conocer y emplear a fondo el sistema de filtrado de la información en el propio nodo, descargando a nuestro «log» de esa tarea (o parte de ella).
  * Tenemos la información de la red RBN disponible algunos nodos, y en el de URE en particular.


