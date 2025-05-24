---
title: "Icom IC-775DSP Hot Switching"
date: 2012-03-16
slug: "icom-acom-hot-switching"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "Acom 1000"
  - "Hot Switching"
  - "IC-775DSP"
---

El temido problema del Icom IC-775DSP Hot Switching, también sufrido con lagunos otros modelos de Icom. Esta semana he recibido un correo de Eric (F4FJH) consultándome sobre el tema, motivo por el cual hago este post ampliando un poco la información que le he proporcionado.

Efectivamente al **combinar el uso del Icom IC-775DSP** (algún otro modelo también) **con el Acom A-1000** (al menos) solemos utilizar la forma de conmutación TX-RX mas sencilla, el conector SEND en el panel trasero ([tipo RCA](http://es.wikipedia.org/wiki/Conector_RCA)). Aparentemente este contacto no esta bien tarado en tiempo, ya que **cuando utilizamos sobre todo portadoras continuas (AM-FM-CW-RTTY)** el amplificador pasa a TX un instante DESPUÉS de que lo haga el transmisor. En amplificadores normales - léase de la vieja escuela - tipo Amritron, Tremendus, etc. no sucede nada (bueno, podemos llegar a estropear el relé de antena), pero en los equipos modernos, con muchas protecciones, se convierte en un problema apareciendo este mensaje de **HOT SWITCHING (conmutación en caliente)**.

Investigando un poco me di cuenta que**Acom** ya hace referencia a este tema y ellos **recomiendan NO UTILIZAR el conector RCA de SEND del panel trasero** , sino conectar el amplificador a uno de los conectores ACC (conectores DIN)

Me tomó de sorpresa y por un momento cundió el pánico, me referí al foro de la URE y ahí [cree yo mismo un hilo](http://goo.gl/mB8sR) donde discutimos la cuestión. Las soluciones no tardaron en llegar.

A modo de resumen de lo allí comentado os dejo las cuatro soluciones:

La primera consiste es hacer PTT directamente sobre el lineal, via el RCA de KEY IN y desde el amplificador conmutar el equipo via el RCA de KEY OUT del Acom. Esta solución puede valer para algunos casos, pero si el amplificador esta apagado o utilizamos un microfono con PTT integrado nos obliga a colocar un [FOOTSWITCH o similar](http://goo.gl/okSXz).

La segunda es utilizar, como recomienda Acom, una de las salidas de ACC, digo una porque tanto en ACC1 como en ACC2 tenemos presente la señal SEND con su respectiva GND (ver gráfico). En esta configuración resolvemos todas las posibilidades, sin embargo he tenido el mensaje de HOT SWITCHING en ALGUNA OCASIÓN AISLADA.

[![Diagrama de conectores ACC1 y ACC2](http://anony.ws/i/RhkIJ.png)](http://anony.ws/i/RhkIJ.png)

Diagrama de conectores ACC1 y ACC2

La tercera opción es la utilización de un [FOOTSWITCH como el Heil FS-2](http://goo.gl/leZr7), un conmutador de TX-RX que tiene dos salidas y que, mecánicamente, secuencia la entrada y salida del amplificador para que este tema no ocurra. La única contra de esta solución es que si se utilizan micrófonos con PTT incorporado (de mano o sobremesa) seguimos con problemas.

La cuarta y última opción, ya para mas manitas y experimentadores, es rebuscar entre los muchísimos circuitos que hay para secuenciar amplificadores, estos son muy frecuentes en MAF, debido a la utilización combinada de previos de RX con ampllificadores y mandar este secuenciador con un y utilizar un [FOOTSWITCH simple, como el Heil FS-3](http://goo.gl/okSXz).

El temido problema del Icom IC-775DSP Hot Switching, solucionado.

Espero haber ayudado.
