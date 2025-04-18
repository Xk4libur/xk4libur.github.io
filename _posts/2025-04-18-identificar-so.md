---
layout: single
title: ¿Cómo puedo identificar un sistema operativo de un equipo externo? (SIN TERMINAR)
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

Se puede ver un detalle importante, el TTL que tiene de valor un 59:

![](/assets/images/identificacion-so/3.png)
