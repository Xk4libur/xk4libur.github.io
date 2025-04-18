---
layout: single
title: ¿Cómo puedo identificar un sistema operativo de un equipo externo?
date: 2025-04-18
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Reconocimiento
tags:
---

Cuando se resuelve una máquina es muy importante identificar que tipo de sistema operativo usa, ya que de esta forma podemos hacernos una idea de que posibles vulnerabilidades puede tener o por lo menos poder empezar a pensar en qué vías potenciales podemos usar.

Hay una forma muy útil de saber que tipo de sistema operativo usa la máquina o sistema objetivo, es usando el comando “**ping**”:

![](/assets/images/identificacion-so/1.png)

En este caso se puede ver un ping a los servidores DNS de Google, esto es solo una prueba para aprender a identificar sistemas operativos en equipos externos:

![](/assets/images/identificacion-so/2.png)

Se puede ver un detalle importante, el **TTL** que tiene de valor un **59**, pero esto del TTL, ¿qué demonios es?.

El **TTL** o **(time to live)** es un mecanismo que determina la cantidad máxima de tiempo o de “saltos” que puede realizar un paquete cuando está en circulación por la red antes de ser descartado.

Cada paquete tiene un valor numérico, y éste se reduce a 1 cuando pasa por un enrutador, en caso de que el paquete llegue a 0, éste se descarta y se envía un mensaje al emisor del paquete.

En el ejemplo anterior, se realizó un ping a un servidor DNS de google y el TTL dió de resultado un 59, cada sistema operativo tiene su TTL correspondiente, y en este caso sería **Linux**, ya que el valor se acerca a **64**.

En caso de que diera un número cercano a **128**, el sistema estaría ejecutando un **Windows**, como es en el siguiente caso:

![](/assets/images/identificacion-so/3.png)

![](/assets/images/identificacion-so/4.png)


Existe este script en Python que nos permite saber que tipo de sistema operativo está usando el sistema objetivo de forma más directa:

[Link al script 'whichsystem'](https://pastebin.com/HmBcu7j2)