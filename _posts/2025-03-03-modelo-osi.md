---
layout: single
title: Modelo OSI y las capas de red
date: 2025-03-05
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Redes
tags:
  - capas
---

## ¿Qué es el modelo OSI?

El modelo OSI es una estructura formada por **7 capas** que se usa para describir todos los procesos de comunicación entre dispositivos dentro de una red de ordenadores. 

Cada capa tiene sus funciones y servicios específicos, y cuando las 7 capas funcionan al completo, permiten la comunicación de todos los dispositivos a través de la red.

## ¿Cómo funciona la comunicación entre los dispositivos de la red?

Cuando enviamos una solicitud desde nuestro ordenador hacia un servidor, esta sale de nuestro equipo a través de un cable físico (si estamos conectados por Ethernet) o por el aire (si usamos Wi-Fi). Desde allí, la solicitud pasa por una serie de intermediarios hasta llegar al servidor de destino.

Una vez procesada, la solicitud sigue el mismo recorrido en reversa para regresar a nuestro equipo.

## ¿Que funciones tiene las 7 capas del modelo OSI?

- 1. **Capa física:** es la capa situada en la parte más baja del modelo OSI, se encarga de la transmisión de datos usando medios fisicos de la red.
Son como los caminos que usan los paquetes para llegar a su siguiente destino en la red

- 2. **Capa de enlace de datos:** es la capa se encarga de asegurar que los paquetes lleguen de forma confiable a la siguiente capa, su función es revisar y corregir los errores o daños que el paquete pueda tener, garantizando de esta forma su correcto envío. 

- 3. **Capa de red:** esta capa tiene la función de elegir la mejor ruta por la que enviar el paquete, también puede decidir que paquetes se enviarán primero, y las mejores rutas a elegir

- 4. **Capa de transporte:** esta capa tiene la función de entregar de forma confiable los datos entre los últimos dispositivos de la red, ofreciendo control de flujo y corrección de errores. En esta capa es donde se usan los protocolos red como TCP y UDP.

- 5. **Capa de sesión:** esta capa crea y mantiene las sesiones de comunicación entre hosts

- 6. **Capa de presentación:** esta capa tiene la función de traducir los datos para que la siguiente capa los pueda usar.

- 7. **Capa de aplicación:** esta capa es la que ofrece los servicios que usan las aplicaciones de los usuarios, ya sea correo electrónico, navegadores web y la transferencia de archivos.

