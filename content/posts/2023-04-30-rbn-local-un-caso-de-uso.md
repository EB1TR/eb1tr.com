---
title: "RBN Local, un caso de uso"
date: 2023-04-30
slug: "rbn-local-un-caso-de-uso"
categories:
  - "Técnicos"
tags:
  - "DX"
  - "DXCluster"
  - "EA1URA"
  - "RBN"
---

Hoy quiero hablarles de la importancia que tiene, para mi, la posibilidad de tener un RBN Local (muy cerca tuyo) y de su utilización de forma cotidiana.

De lo que es la red RBN ya os he hablando en [otro post de esta mismo blog](https://www.eb1tr.com/dxcluster-y-rbn/). Hoy la idea es hablar de un «caso de uso» concreto, muy concreto.

Gracias al trabajo que realizan miembros de URE Asturias tenemos [disponible uno de estos receptores en el Principado de Asturia](https://www.ea1ura.com/189-ea1ura-skimmer)s. Ofrece grandes posibilidades para concursos y DX ya que tenemos la posibilidad de disponer de un receptor que nos va a anunciar todas las estaciones que se estén recibiendo en Asturias en todas las bandas.

Si bien es verdad que los anuncios generados por este receptor van a la red y podemos aprovecharlos de esa forma hoy veremos que tenemos una posibilidad adicional. Los RBN pueden disponer (y el de Asturias lo tiene) de un acceso TELNET para que podamos disponer del flujo de anuncios sin pasar por el resto de la red RBN ni DXCluster.

#### Uso en Logger32

Es un software espectacular, no me canso de decirlo. En L32 tenemos una ventana donde configuramos la conexión al nodo TELNET que sea de nuestra preferencia, allí podemos tener filtros y diferentes opciones activadas, pero hay mas cosas disponibles.

Concretamente hay una «solapa» denominada inicialmente como «Local Host» que está específicamente preparada para recibir un segundo flujo de datos provenientes, justamente, de un RBN.

![](https://www.eb1tr.com/wp-content/uploads/2023/04/localhost.png)

Datos recibidos directamente por el RBN EA1URA

Es en esa ventana donde debemos conectar con el servidor TELNET del RBN de Asturias, los datos de conexión son los siguientes:
    
    
    rbn.ea1ura.com:7300

Los anuncios recibidos por esta vía se van a mezclar con lo que se reciben por el nodo «normal» que hemos elegido y, en la ventana de SPOTS, se pueden diferenciar usando, por ejemplo, otro color. En mi caso los SPOTS «normales» tienen una tipografía blanca y los recibidos desde el RBN están en color rojo.

![](https://www.eb1tr.com/wp-content/uploads/2023/04/cluster.png)

Anuncios «normales» y RBN Locales diferenciados por su color

Es frecuente, muy frecuente, que el disponer de esta ayuda te haga llegar a los DX en pocos segundos desde el primer CQ, lo que te coloca en una posición adelantada al resto de estaciones.

Espero que os sea de utilidad. 😉

 
