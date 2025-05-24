---
title: "Software de Radio en EB1TR"
date: 2017-12-10
slug: "software-de-radio"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "Dimension4"
  - "EB1TR"
  - "Ham Radio Deluxe"
  - "Logger32"
  - "N1MM+"
  - "Software"
  - "Software de Radio"
  - "VE7CC"
  - "VoaProp"
  - "VPSE"
  - "WSJT-X"
---

Este post tiene como objeto, simplemente, describir mi experiencia en la busqueda de software de radio para lograr un funcionamiento eficiente con la mayor versatilidad posible y haciendo que cada pieza «del puzzle» lo haga por razones MUY concretas.

### ¿Para que uso de la Estación?

Es una de las primeras cosas que me gustaría aclarar. Bajo ningún punto de vista se trata de una instalación de las que «quitan el hipo», simplemente intenta ser un lugar muy cómodo en el que me permito hacer muchas y muy variadas actividades como DX, RadioEscucha, concursos a nivel súper básico, modos digitales, CW, etc.

A nivel de software creo que se puede tomar como solución analoga para una gran parte de los Radioaficionados que tienen una actividad «generica» de nuestro hobby, por lo que creo puede aportar alguna idea a la aplicación que cada uno de vosotros hace en el día a día.

### Software de Sistema

##### VPSE

Se trata de un emulador de puerto serie virtual, a día de hoy, una pieza fundamental en la estación de radio. La gran variedad de programas que utilizamos de forma cotidiana para atender las necesidades de nuestro transceptor es tan grande que es necesario para «multiplexar» esa conectividad y hacer que varios programas puedan acceder al «puerto COM», y hacerlo de forma nativa sobre el componente de hardware es imposible. Este programa genera un puerto serie virtual, conectado al fisico, que permite a varios programas acceder al mismo. En mi caso acceden a el: Logger32, VE7CC Cluster (una o varias instancias), Ham Radio Deluxe y, eventualmente, N1MM+.

[![Vista de "Virtual Port Serial Engine"](https://www.eb1tr.info/wp-content/uploads/2017/12/vpse-300x176.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/vpse.jpg)

Vista de «Virtual Port Serial Engine»

##### Dimension4

Mantener la hora del PC actulizada es importante a la hora de tener corriendo varios programas en lo que la hora es importante. Sin lugar a dudas que guardar QSOs correctamente lo es, pero desde la irrupción del Wisper, WSJT y, el ahora inbatible, FT8 se hace excluyente. Windows hace esta función por defecto, pero la eficiencia no es su fuerte por lo que se hace necesario «tirar» de programas como NetTime (gracias Tony/EA5BY) o [Dimension4](http://www.thinkman.com/dimension4/). En mi caso actualizo la hora (con la opción que elija de las anteriores) contra el servidor SNTP hora.roa.es, servidor local que tiene un muy baja latencia.

[![Asi luce "Dimension 4", cuando se borran los servidores por defecto y dejamos solo el que nos interesa.](https://www.eb1tr.info/wp-content/uploads/2017/12/dimension4-300x273.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/dimension4.jpg)

Asi luce «Dimension 4», cuando se borran los servidores por defecto y dejamos solo el que nos interesa.

##### SublimeText3

Los radioaficionados tenemos un formato de archivos para intercambio de información que es super interesante, el ADIF. Aunque hay algun programa para gestionar este formato de forma «gráfica» el poder hacerlo a «bajo nivel» es muchas veces mas eficiente y se pueden hacer cosas increíbles a nivel de reemplazo de textos por expresiones regulares y demas.[ SublimeText3](https://www.sublimetext.com/3) y [Notepad++](https://notepad-plus-plus.org/) son programas de edicion de código, en principio, con muchas funcionalidades de este estilo.

[!["Sublime Text" lo abro según necesidad.](https://www.eb1tr.info/wp-content/uploads/2017/12/sublime-text-300x188.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/sublime-text.jpg)

«Sublime Text» lo abro según necesidad.

##### OwnCloud (o cualquier otra nube)

Se trata de una medida de seguridad, sobre todo de cara a asegurar la integridad de los datos mas importantes de los que disponemos. Configuración de distintos programas, backups del libro de guardia, distintos ficheros de definición de equipos, etc.; es sumamente importante tenerlos a buen resguardo y, disponer de ellos en la nube, puede ser de gran utilidad.

OwnCloud es una «especie de CMS» que se instala en el servidor web y puede almacenar información, tiene clientes para iOS, Android, Windows, GNU/Linux y OSX. Puede ser reemplazado por servicios de terceros, como Google Drive, DropBox u otros.

[!["OwnCloud" corriendo como servicio general de almacenamiento.](https://www.eb1tr.info/wp-content/uploads/2017/12/owncloud-300x246.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/owncloud.jpg)

«OwnCloud» corriendo como servicio general de almacenamiento.

##### Audacity

Muchas veces me veo en la necesidad de hacer tomas de audio de las recepciones, tanto en HAM como haciendo SWL. [Audacity](http://www.audacityteam.org/) es una soluciones gratuita, sencilla y efectiva que me permite fácilmente hacer tomas de audio y exportarlas a MP3 o cualquier otro formato para guardar o publicar.

[!["Audacity", normalmente en monitor principal \(22"\).](https://www.eb1tr.info/wp-content/uploads/2017/12/audacity-300x194.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/audacity.jpg)

«Audacity», normalmente en monitor principal (22″).

### Software de Radio

##### Ham Radio Deluxe

No voy a centrarme en explicar que es Ham Radio Deluxe por dos motivos, uno que es un programa ampliamente conocido, el segundo porque es MUY grande, hace DEMASIADO y lo uso para MUY poco. En mi caso particular, y es discutible, me gusta tener de forma grafica algunos de los controles del transceptor. Mi transceptor tiene «pocos» controles fisicos, por lo que se hace «comodo» tener esta utilidad. Por otro lado se hace indispensable en mi caso para la utilizacion de WSJT-X. La gestion del CAT de WSJT hace que «no le guste» tener el CAT en el mismo puerto que el control de PTT, por lo que seleccionando en WSJT-X «CAT en Ham Radio Deluxe» y PTT en «COM X» funciona perfectamente y no se entera que estan en el mismo COM. El resto de funciones de Ham Radio Deluxe no las utilizo, simplemente me olvido de ellas.

[!["Ham Radio Deluxe", normalmente corriendo en el monito secundario \(19"\).](https://www.eb1tr.info/wp-content/uploads/2017/12/hrd-300x240.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/hrd.jpg)

«Ham Radio Deluxe», normalmente corriendo en el monito secundario (19″).

##### Logger32

Sin lugar a dudas que [Logger32](http://www.logger32.net/) es uno de los mejores programas para libro de guardia, es gratuito y con una linea de desarrollo que le ha convertido en uno de los mas populares y eficientes que podemos encontrar. Entre las grandes ventajas que podemos enumerar (no pretendo nombrarlas todas) podemos destacar: control de dos transceptores, control para conmutacion de antenas, principales diplomas cargados, posibilidad de generar nuevos, cluster, mapas, integración UDP con WSJT-X. Lo hace todo, y lo hace MUY bien, poco mas podemos pedir.

Detras de él hay una gran comunidad de usuarios y un grupo de desarrollo que aporta funcionalidades a la propia aplicación así como utilidades paralelas que funcionan a traves de una «especie API» con la que interactuan para un sinfín de posibilidades.

[!["Logger32" normalmente corriendo en el monitor principal \(22"\)](https://www.eb1tr.info/wp-content/uploads/2017/12/logger32-300x188.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/logger32.jpg)

«Logger32″ normalmente corriendo en el monitor principal (22»)

##### N1MM+

Dentro de la tecnología en software utilizada por las estaciones de concursos hay, basicamente, dos opciones: WinTest y N1MM+.

En mi caso, y desde hace mucho tiempo, he/hemos (en ED1B) optado por la solucion [GRATUITA N1MM+](https://n1mm.hamdocs.com/tiki-index.php), representa todo lo que uno necesita del software con una gran capacidad de hacer modular todos los componentes ajustandolos al gusto de cada uno de los operadores. En estaciones «Multi» cada uno de los operadores determina las ventanas y la posicion de las mismas, que son respetada cada vez que tomar su turno. **EXCELENTE**. Como he dicho antes, no me voy a parar a explicar cada una de las funciones que tiene el programa, solo saber cual utilizo y las principales razones, que son: ES GRATUITO, modular, muy ligero, gran cantidad de concursos disponibles y una comunidad MUY amplia de desarrollo que lo hace tener _releases_ que van mejorando constantemente las funcionalidad y posibles fallos.

[!["N1MM+", siempre en monitor principal \(22"\).](https://www.eb1tr.info/wp-content/uploads/2017/12/n1mm-300x188.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/n1mm.jpg)

«N1MM+», siempre en monitor principal (22″).

##### VE7CC Cluster

Es un cliente Telnet para DX Cluster. Sencillo. Aunque, como veremos, tiene múltiples ventajas que lo hacen, a mi modo de ver, indispensable. [VE7CC Cluster](http://www.bcdxc.org/ve7cc/) se puede conectar a multiples host con lo que podemos tener la certeza de que es MUY DIFICIL que un spot se pierda en todos ellos, en mi caso conecto a 5 clusters distintos y VE7CC genera un «flujo comun» de ellos que lo distribuye a traves de un servidor telnet local al que Logger32 y N1MM+ se conectan, esto es una ventaja fundamenteal a la hora de gestionar las conexiones ya que la configuracion de los programas de log nunca cambia y se desentienden de desde donde vienen esos datos. VE7CC filtra los spots que llegan a el seteando esos filtros directamente en el servidor de cluster, por lo que se ahorra ancho de banda (importante en algunos entornos) y causando menor utilizacion de buffers.

A todas estas caracteristicas le sumamos que es multiproceso, significa que podemos tener varias instancias de VE7CC abiertas con la ventaja de aplicar distindos filtros a cada uno de ellos. La última GRAN ventaja de VE7CC, aunque solo para usuarios de Elecraft K3 (o familia), es que VE7CC puede conectar por CAT con el transceptor para que un click en un SPOT nos envia directamente a la frecuencia designada; esta función esta presente en el software de log (Logger32 o N1MM+) pero, como explique antes, al ser multiproceso, es posible tener un VE7CC buscando solo SPOTS en 40 metros SSB de DME´s, lo que normalmente se nos quedaría perdido en la ventana de cluster del programa de log, aqui se vería en unas pocas líneas.

En otro [post anterior](https://www.eb1tr.info/dxcluster/) planteo la configuración concreta.

[!["VE7CC Cluster", normalmente corriendo en el monitor secundario \(19"\).](https://www.eb1tr.info/wp-content/uploads/2017/12/ve7cc-300x241.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/ve7cc.jpg)

«VE7CC Cluster», normalmente corriendo en el monitor secundario (19″).

##### WSJT-X

Es una de las últimas irrupciones, [WSJT-X](https://physics.princeton.edu/pulsar/k1jt/), con su modo estrella (el FT8), esta revolucionando la radio. Cantidades ingentes de operadores estan en todas las bandas permanentemente y, su capacidad en condiciones adversas, hacen que QSOs impensables en otros modos, aqui sean corrientes. No es la única opción para trabajar JTx o FT8, gracias a Arsenio/EA1AHY he probado [JTDX](http://jtdx.tech/) que tiene algunas mejoras en la interfaz gráfica y soluciones un poco mas «cuidadas». Es probable que merezca la pena hacer una comparativa entre ellas, pero ahí lo dejo, simplemente y que cada uno de vosotros pruebe y lo comente.

Un dato MUY importante, y al menos que me ha pasado, es que el programa (en realidad ambos) se llevan «un poco mal» con tener el CAT en un puerto y el PTT en el mismo, muchos cuelgues de CAT, etc. Por lo que la solución a los mismo ha sido «atacar» el CAT del equipo de forma «indirecta» a traves de Ham Radio Deluxe. Es una solución un poco controversial, pero en mi caso, donde hay muchas aplicaciones tirando de los datos de CAT, y aportando en ellos, ha sido la que mejor resultado me ha dado.

[!["WSJT-X", , normalmente corriendo en el monitor secundario \(19"\).](https://www.eb1tr.info/wp-content/uploads/2017/12/wsjt-x-300x240.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/wsjt-x.jpg)

«WSJT-X», , normalmente corriendo en el monitor secundario (19″).

##### VoaProp

Es una de esas utilidades muy necesarias, se trata de un software que da una idea, según condiciones de propagacion y tipo de instalación, de las areas de covertura y la intensidad aproximada de las señales. Desarrollo de G4ILO, podemos bajarlo de forma gratuita [desde su web](http://www.g4ilo.com/voaprop.html) y solo necesitamos tener instalados los ficheros de HFProp, que son los que hacen internamente el calculo que luego es representado en un mapa de VoaProp.

[!["VoaProp", lo arranco según necesidad.](https://www.eb1tr.info/wp-content/uploads/2017/12/voaprop-300x218.jpg)](https://www.eb1tr.info/wp-content/uploads/2017/12/voaprop.jpg)

«VoaProp», lo arranco según necesidad.

 

Como he comenzado, quiero recordarte, que se trata de una configuracion MUY personal, en la que pretendo darte ideas de posibles soluciones a temas cotidianos en nuestra aficion. Si te sientes identificado, quieres comentar tu punto de vista o cualquier otra cosa, no dejes de escribir un comentario.

¡Buena Radio!
