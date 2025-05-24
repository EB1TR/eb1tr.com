---
title: "Jugando con «REGEX» en el DXCluster"
date: 2022-07-22
slug: "regex-dxcluster"
categories:
  - "Curiosidades"
  - "Técnicos"
tags:
  - "DXCluster"
  - "DXSpider"
  - "HamDevOps"
  - "REGEX"
---

En otros post de este mismo blog hablo de varios aspectos del DXCluster como [tips](https://www.eb1tr.com/tips-dxcluster/) o el uso de [RBN](https://www.eb1tr.com/dxcluster-y-rbn/) entre [otros.](https://www.eb1tr.com/?s=dxcluster)

Hoy vamos a experimentar «un poco mas allá» aplicando algunas «reglas» particulares como las que aceptan los Nodos de la red de DXCluster basados en DXSpider, como los de URE. 😉

Antes que nada tenemos que poner un poco de contexto y poner en claro algunas nociones básicas.

#### Que es una REGEX

Una REGEX (expresión regular) es una de las funciones mas utilizadas en programación. Se pueden utilizar en muchos ámbitos pero es especialmente relevante cuando tenemos un volumen de datos muy grande para analizar y queremos «filtrar» o «limitar» los resultados que tenemos o queremos visualizar.

Una REGEX es un «patron» que le indicamos al sistema para que busque la información que coincida con dicho patrón.

Un ejemplo:

Tenemos las siguientes palabras: blanco, negro, gris, verde

Si le decimos «al sistema» que muestre las palabras que coincidan con la REGEX «gro» el sistema nos devolverá «negro», si cambiamos la expresion regular y le indicamos al sistema que nos devuelva las palabras que coincidan con «gr» nos devolverá «negro» y «gris».

Existen muchas formas de construir las expresiones regulares, indicando si el patron esta al principio, al final, en medio, precedido de números, letras… Un sinfín de variables que son muy potentes en el análisis de datos.

#### ¿Se te fue la olla?

No, no tan rápido. Esta cuestion no escapa a los programadores, obviamente. Es por eso que se ha introducido el soporte de expresiones regulares en el DXSpider.

En la información que viaja por la red de DXCluster tenemos un campo que ofrece mucha información, aunque lo «anárquico» de su uso lo hace -a veces- inserbible, pero es un «campo de rosas» para la práctica de expresiones regulares y buscar spots con una finalidad determinada.

El campo del que hablamos es el campo «comentarios» o «info», en la documentación técnica del DXSpider.

#### Unión REGEX con DXSpider

Cuando interactuamos con el nodo al que nos conectamos de la red de DXCluster lo hacemos conectando a través de TELNET, de esta manera podemos dar comandos, como vimos en [otro post](https://www.eb1tr.com/tips-dxcluster/) para buscar o filtrar informacion.

En aquel caso nos basabamos en campos como la Zona CQ, Banda, Modo, etc. Esta vez nos centraremos en el campo «info».

Lo primero que vamos a indicar es que cuando busquemos (o filtremos) por el campo «info» las REGEX van declaradas dentro de llaves «{}», y dentro el patrón que queremos buscar.

Veremos, a continuación la diferencia entre buscar «sh/dx info dB» y sh/dx info {\ddB}

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-14-a-las-23.09.04.png)

La diferencia de resultados radica en que en la izquierda se busca «dB», pero a la derecha se busca «dB» precedido por dígitos (números) que en una REGEX se pueden representar como «\d».

#### Ejemplos FTx (FT8 y/o FT4)

Este modo, unido a la red RBN, genera una cantidad enorme de datos. Datos que utilizaremos y otros que realmente molestan. Vamos a trabajar un poco con el concepto de REGEX y patrones que se repiten en los anuncios (automáticos o no) de esos modos.

Así podemos hacer una REGEX para buscar SPOTS en FTx, por ejemplo:
    
    
    sh/dx info {FT8|FT4}

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.02.21.png)

Podemos afinar mas la búsqueda:
    
    
    sh/dx info {FT8|FT4} on hf

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.03.35.png)

#### REGEX si, pero NO SÓLO en las búsquedas, las aplicamos a filtros

La importancia de estos comando y la potencia de las REGEX no radica, simplemente, en hacer búsquedas. **¡Las REGEX puden usarse en FILTROS!** , filtros la mar de complejos, donde podamos relacionar una o varias REGEX, con otros campos como modos o bandas.

Muchas veces he leído en Redes Sociales, Foros, etc. de personas a las que no les gusta el FT8, salvo que sea en VHF donde SÍ lo utilizan.

Con este sencillo ejemplo nos vamos a borrar de un solo comando cualquier SPOT en FT8, salvo que esté fuera de HF.
    
    
    reject/spot 1 info {FT8.*\d.*dB|FT4.*\d.*dB} and on hf

#### REGEX aplicada a los Diplomas EA

Hay operadores que sólo se dedican a estos diplomas y, aquí también, las REGEX nos pueden ayudar, Y MUCHO.

**Búsqueda de estaciones que han sido anunciadas para el Diploma DME:**
    
    
    sh/dx 25 info {DME.\d}

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.16.03.png)

**Búsqueda de estaciones que han sido anunciadas para el Diploma DMVE:**
    
    
    sh/dx 25 info {MV[A-Z].\d}

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.18.15.png)

**Búsqueda de estaciones que han sido anunciadas para el Diploma DEE:**

Éste del Diploma Ermitas es un buen ejemplo. La REGEX a utilizar es «{E[[A-Z]-\d}» el problema es que tiene coincidencias con muchas otras referencias. Mirad:

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.35.42.png)

Para evitar SPOTS cuya estación anunciada esté fuera de España agregamos «and dxcc ea,ea6,ea8,ea9» y luego eliminamos también los anuncios que contengan «info POTA,EAFF,IOTA,{MUE[A-Z]}», de ahí esta expresión:
    
    
    sh/dx 25 info {E[A-Z].?\d} and dxcc ea,ea6,ea8,ea9 and not info POTA,EAFF,IOTA,{MUE[A-Z]}

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-15-a-las-0.31.47.png)

**Búsqueda de estaciones que han sido anunciadas para el Diploma DEFE:**

Aquí tenemos efectos similares que en el DEE, por lo tanto también tenemos que «afinar» la búsqueda restringiendo el DXCC. La REGEX podría quedar como esta:
    
    
    sh/dx 25 info {EF[A-Z].\d} and dxcc ea,ea6,ea8,ea9

 

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-22-a-las-1.11.38.png)

**Búsqueda de estaciones que han sido anunciadas para el Diploma DCE:**
    
    
    sh/dx 25 info {C[A-Z].\d} and dxcc ea,ea6,ea8,ea9

![](https://www.eb1tr.com/wp-content/uploads/2022/07/Captura-de-Pantalla-2022-07-22-a-las-1.09.52.png)

En este ejemplo, en el DCE, la verdad es que habría que trabajar bastante el filtro mas adecuado. A simple vista ya se puede observar que hay bastante «ruido» en los resultados.

#### Conclusiones

  * La implementacion de REGEX en DXSpider no es «perfecta». Se trata de una «interpretación» de las posibilidades que tienen las REGEX. Algunas funciones/opciones no se pueden utilizar.
  * Tenemos que trabajar las REGEX de tal forma de mejorar el número de resultados correctos frente a los incorrectos.
  * Cuando trabajamos con «campos libres» -como lo es el campo de información- nos vemos «obligados» a filtrar y evolucionar el «algoritmo» de filtrado según vamos viendo los resultados.



Las expresiones que hemos publicado se trata, meramente, de referencias, para empezar a jugar y que podemos/debemos evolucionar teniendo en cuenta resultados.

Si quieres aprender sobre expresiones regulares -REGEX- te aconsejo que des una vuelta por la red, hay mucha informacion y diferentes herramientas para probarlas online; como ésta:

<https://4geeks.com/es/lesson/regex-tutorial-regular-expression-examples-es>
