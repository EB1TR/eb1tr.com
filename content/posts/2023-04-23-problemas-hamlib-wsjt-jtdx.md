---
title: "Problemas de HamLib en WSJT/JTDX (solución)"
date: 2023-04-23
slug: "problemas-hamlib-wsjt-jtdx"
categories:
  - "Técnicos"
tags:
  - "FT4"
  - "FT8"
  - "HamLib"
  - "JTDX"
  - "Software"
  - "WSJT-X"
---

Es de todos -o casi todos- conocido que WSJT y JTDX «pueden» dar problemas en la gestión de la conexión de datos a la radio, el conocido CAT.

En este post veremos en que entornos suele dar problemas, las razones de los mismos y la solución.

#### Entornos Problemáticos

En mi caso, como explico en [esta entrada sobre mis equipos](https://www.eb1tr.com/estacion/equipos/) o en [esta sobre el software que uso](https://www.eb1tr.com/software-de-radio/), uso un Elecraft K3 y Logger32 como libro de guardia. La conexión se hace a través de VSPE para «multiplexar» el acceso al puerto y poder «atacar» la radio con mas de una aplicación, y este es uno de los motivos de fallo.

Por extensión podemos asumir que, cuando a través del puerto como físico hay mas de una comunicación realizándose, puede haber problemas de colisiones o respuestas no interpretadas.

![](https://www.eb1tr.com/wp-content/uploads/2023/04/rig-failure.jpg)

#### Las Razones

Bueno, ya se han adelantado, colisiones y paquetes no interpretados -por cualquier razón-.

Tenemos que entender que, en el contexto mencionado, el equipo «escucha» peticiones de información y las responde. Cuando las responde estas respuestas con información son enviadas a **todas** las aplicaciones que están conectadas al puerto COM virtual, el multiplexado.

Aquí se pueden dar algunas casuísticas interesantes:

  1. Que un programa «flipe» (se sorprenda y falle) porque recibe una respuesta de algo «que no preguntó».
  2. Que esa respuesta, ademas, no esté en el SET de comandos que la librería tiene implementada.



Debo reconocer que sufrí estos problemas bastante tiempo, aunque no soy un usuario intensivo de FT8, me ha dado mas de un dolor de cabeza (por testarudo, mas que nada) y me llevó a implementar soluciones «poco ortodoxas».

La primera fue utilizar a HamRadio Deluxe como «abstracción» del problema. WSJT/JTDX «hablaban» con la radio a través de HRD, **una auténtica chapuza**.

La segunda, y que perduró mucho mas tiempo, fue utilizar OmniRig como capa de abstracción.

He oído que hay gente que pone FLRig o cosas similares; incluso apagar el CAT del libro de guardia y alternar uno u otro. Todas son válidas, pero si tenemos menos programas funcionando, todo irá mas fluido.

#### La Solución

Hasta la versión 158 de JTDX la librería HamLib venía «empotrada» en la compilación -y era vieja- lo que hacía imposible una actualización de la misma, pero desde la 158 la librería viene separada. Gracias a ello podemos descargarla y actualizarla desde aquí (tened en cuenta si es 32 o 64 bits):

W32: [32 bit libhamlib-4.dll](https://n0nb.users.sourceforge.net/dll32/libhamlib-4.dll)

W64: [64 bit libhamlib-4.dll](https://n0nb.users.sourceforge.net/dll64/libhamlib-4.dll)

Se baja el fichero ZIP y se reemplaza directamente la DLL.

![](https://www.eb1tr.com/wp-content/uploads/2023/04/hamlib.jpg)

En WSJT parece que la cosa es mas sencilla. **Hice una instalación limpia** y, aparentemente, viene con la última versión de HamLib. Esto se debe chequear y, en su caso, intentar la misma solución que JTDX, meter la DLL directamente.

Espero que os sea de utilidad. 😉
