---
title: "DRM (Digital Radio Mondiale)"
date: 2019-12-08
slug: "drm-digital-radio-mondiale"
categories:
  - "SWL"
  - "Técnicos"
tags:
  - "Digital Radio Mondiale"
  - "DRM"
  - "Onda Corta"
  - "Short Wave"
---

Hoy haré un post donde lo verdaderamente importante es comenzar con lo mas básico acerca de este modo de emisión. El DRM (Digital Radio Mondiale) es un conjunto de tecnologías de emisión que permiten un mejor aprovechamiento espectral del éter, en las bandas de onda corta -las que nos ocupan normalmente- se considera que el nombre correcto del modo es DRM30, indicando que es en frecuencias inferiores a 30MHz.

El DRM se ha diseñado con la premisa de que las emisoras existentes pudiesen utilizar los mismos equipos transmisores que los que utilizaban en las emisiones en analogico, aunque ésto -por diferentes razones- no es posible o lo mas correcto.

#### Algunos datos técnicos del DRM

Las velocidades oscilan entre los 6,1kbits y los 38,4kbits con un ancho de banda de unos 10KHz. El codec, al menos uno de ellos, que se utiliza en las emisiones DRM es el MPEG-4 HE-AAC, se trata de un códec muy adecuado para la utilización en bandas de onda corta, que predominantemente se envía voz y ocasionalmente música. Por otro lado el DRM permite multiplexar canales, por lo que en una misma emision (10KHz de BW) podemos tener uno o mas canales de audio.

Aparte de los canales de audio, al estilo del RDS -para entendernos-, el DRM envía alguna información complementaria (texto) que los receptores o decodificadores interpretan y nos muentran en pantalla.

[![espectro drm radio rumania](https://www.eb1tr.com/wp-content/uploads/2019/12/drm-rri-1024x562.png)](https://www.eb1tr.com/wp-content/uploads/2019/12/drm-rri.png)

Captura del espestro en la emisión de Radio Rumanía Internacional.

#### Recepción en DRM

Al ser un modo digital, evidentemente, la recepción de estas emisiones resultan algo mas complejas que las que hacemos comunmente en modulación de amplitud. En este caso tenemos dos opciones, la utilizacion de un receptor standalone -dedicado- o lo hacemos mediante la utilización de software en un PC.

##### Receptor DRM standalone

No tenemos muchas opciones, en la propia web del estandar tenemos una sección para la [promoción de productos](https://www.drm.org/products/). He realizado una búsqueda rápida en eBay y en Amazon sin resultados, al menos en este tipo de receptores. Figuran varios receptores aunque sólo dos de ellos tienen la web funcional:

![](https://www.eb1tr.com/wp-content/uploads/2019/12/titus-II-300x173.jpg) | ![](https://www.eb1tr.com/wp-content/uploads/2019/12/chino-300x283.jpg)  
---|---  
<https://titusradio.com/> | [Alibaba](https://www.alibaba.com/product-detail/Digital-Radio-Mondiale-DRM-Radio-Receiver_11547499.html?fullFirstScreen=true)  
  
##### Receptor DRM por software

Aquí el abanico es mucho mayor y, por lógica, las opciones mucho mas económicas y viables. En este caso se trata de obtener la señal de audio de 10KHz de ancho de banda, por el medio que tengamos disponible, y apartir de ahi apliquemos ese audio a algún software que pueda demodular la señal y la reproduzca en los altavoces del PC.

##### Aquello de «por el medio que tengamos disponible»

Tenemos varias opciones, y muchas mas que se os pueden ocurrir, aqui os voy a hablar esencialmente de dos, una que NO me dio resultado -razones obvias- y la otra que me ha funcionado correctamente.

La primera de ellas es recibir la señal deseada a traves de un equipo de radio, esto es bastante problemático ya que no hay muchos receptores de mercado que nos permitan un paso a traves del sistema de filtros de 10KHz o mas, estamos intentando hacer lo contrario de lo que para han sido diseñados.

En mi caso aplicando al filtro mas ancho del Elecraft K3 (5KHz) evidentemente no he logrado absolutamente nada, sin embargo hay algún receptor en el que me encantaría hacer la prueba, como el TS-850* (tiene un paso de 12KHz en la segunda FI -455KHz- y capacidad de deshabilitar el filtro en la primera -8.83KHz- ) lo que, técnicamente, le daría la capacidad del paso de los 10KHz necesarios.

Es probable que el TS-950 esté en las mismas condiciones, o el TS-450, pero el TS-850 lo he abierto a 12KHz.

La segunda tiene que ver con los receptores SDR, estoy metiendo muchas horas en este tipo de receptores y es un mundo apasionante, capacidades increíbles y una flexibilidad que «mete miedo». Para poder recibir DRM con un SDR necesitamos, en el setup que tengo hecho en mi estación de radio, los siguientes elementos:

**Receptor: AirSpy HF+ Discovery** ([os hable de él aquí](https://www.eb1tr.com/airspy-hf-discovery/))

Es el encargado de hacer el muestreo de las frecuencias de radio y convertirlas en señales que el software SDR sea capaz de demodular.

**Software SDR: SDR# 1.0.0.1732** ([web del creador](https://airspy.com/download/))

Es el que realizará la tarea de demodular las señales provenientes del receptor y proveer audio ya demodulado al software que aplicará el codec adecuado para recibir la señal audible.

En este caso SDR# tendrá como «dispositivo de entrada» el receptor SDR y como «dispositivo de salida» una interfaz de audio virtual que tiene como único objeto el poder ser utilizado como dispositivo de entrada en la cadena, algo mas adelante.

**Virtual Audio Cable: VB-AUDIO Software** ([web](https://www.vb-audio.com/Cable/))

Este programa nos permite la creación y utilizacion de una interfaz de audio virtual que será el vínculo entre el flujo de salida del software SDR y la entrada al decodificador de DRM.

**Software DRM: Dream 2.1.1** ([descarga](https://sourceforge.net/projects/drm/files/dream/))

Esta es la última pieza de software. En mi caso NO he podido funcionar con la version 2.2 (la última que figura en la web) por la falta de algunas librerías del sistema, estoy ejecutando Windows 10 x64 PRO. Probando la versión que os detallo mas arriba (2.1.1) no he tenido problema alguno, por lo que uso esta opción hasta tener una solución a la última.

Lo mas importante de este software es configurar correctamente las interfaces de entrada y salida. Insisto, tenemos que configurar como dispositivo de entrada el audio virtual que viene del software demodulador (SDR#) y como dispositivo de salida el que tengamos disponible para el uso de altavoces/auriculares.

[![dream dispositivo de entrada](https://www.eb1tr.com/wp-content/uploads/2019/12/dream-audio-in-300x169.png)](https://www.eb1tr.com/wp-content/uploads/2019/12/dream-audio-in.png)Dispositivo de audio de entrada. |  [![dream dispositivo de salida](https://www.eb1tr.com/wp-content/uploads/2019/12/dream-audio-out-300x168.png)](https://www.eb1tr.com/wp-content/uploads/2019/12/dream-audio-out.png)Dispositivo de audio de salida.  
---|---  
  
#### Y por último, ¿como suena el DRM?

##### Captura de SDR#

##### Captura de Dream

#### ¿Cuando y donde tenemos DRM?

Nuevamente nos vamos a remitir a la web oficial del estandar, en ella teneis una [sección dedicada a difundir las emisoras](https://www.drm.org/what-can-i-hear/broadcast-schedule-2/), frecuencias y horarios disponibles. **No olvideis el detalle de que se promociona la frecuencia CENTRAL de la emision, pero tendreis que poneros 5KHz por debajo de la frecuencia publicada en modo USB y con un ancho de banda de 10KHz.**

Espero que os sirva, si teneis alguna duda o comentario no dudéis en dejarlo por aquí, buenas escuchas.
