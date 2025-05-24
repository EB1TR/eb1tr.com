---
title: "AirSpy HF+ con OpenWebRX (y OpenWebRXPlus) en Docker"
date: 2024-08-17
slug: "airspy-hf-con-openwebrx-y-openwebrxplus-en-docker"
categories:
  - "Artículos"
  - "Técnicos"
tags:
  - "AirSpy"
  - "Docker"
  - "Docker Compose"
  - "HamDevOps"
  - "OpenWebRX"
  - "OpenWebRXPlus"
  - "SpyServer"
---

Últimamente me encuentro trabajando bastante con un receptor SDR remoto, el AirSpy HF+. De momento lo estaba utilizando con el servidor SpyServer para conectar con SDRSharp como cliente.

Aunque **la performance, calidad y rendimiento de la solución AirSpy HF+ + SpyServer + SDRSharp es absolutamente incuestionable** , ¿porque no probar mas cosas?.

#### Orden, ante todo, orden…

Los amigos **Jose/EA1AIW** y **Roberto/EB1HHA** (si, me han picado) están probando cosas con OpenWebRX y, después de ver algunas de las capacidades, me picó la curiosidad.

En el remoto hay un Debian (servidor para varias cosas de la estación) y mi intención es «ensuciarlo» lo menos posible, he aqui el motivo de este post.

Estoy corriendo OpenWebRX y OpenWebRXPlus (de forma alternada) de forma «contenerizada».

En la web de los desarrolladores tenemos información de como correrlos:

  * OpenWebRX: <https://hub.docker.com/r/jketterl/openwebrx>
  * OpenWebRXPlus: <https://hub.docker.com/r/slechev/openwebrxplus>



La finalidad del post es compartir una forma alternativa, testeada, de poder correr dichos contenedores de forma mas ordenada, documentada y automatizable, a través de Docker Compose.

#### Docker Compose para OpenWebRX
    
    
    services:
      owrx:
        image: jketterl/openwebrx-airspy
        container_name: owrx
        devices:
          - "/dev/bus/usb"
        ports:
          - "8073:8073"
        volumes:
          - "openwebrx-settings:/var/lib/openwebrx"
        restart: unless-stopped
    
    volumes:
      openwebrx-settings:

#### Docker Compose para OpenWebRXPlus
    
    
    services:
      owrxp:
        image: slechev/openwebrxplus
        container_name: owrxp
        devices:
          - "/dev/bus/usb"
        ports:
          - 8073:8073
        volumes:
          - "/opt/owrx-docker/var:/var/lib/openwebrx"
          - "/opt/owrx-docker/etc:/etc/openwebrx"
          - "/opt/owrx-docker/plugins:/usr/lib/python3/dist-packages/htdocs/plugins"
        restart: unless-stopped

**Antes de correr ese fichero debemos crear las carpetas que vamos a «bindear»:**
    
    
    sudo mkdir -p /opt/owrx-docker/var /opt/owrx-docker/etc /opt/owrx-docker/plugins/receiver /opt/owrx-docker/plugins/map

**Para crear un usuario, en cualquiera de los casos, debemos correr:**
    
    
    docker exec -it [nombre_del_contenedor] openwebrx admin adduser [nombre_usuario]

**Aquí el resultado:**

![](https://www.eb1tr.com/wp-content/uploads/2024/08/openwebrxp.jpg)

OpenWebRXPlus en la banda de 40 metros, el receptor es un AirSpy HF+ y la antena es un dipolo de 1/2 onda.

Espero que lo disfrutes, no dejes de contactar ante cualquier duda.

Buenas escuchas, 73 y DX!
