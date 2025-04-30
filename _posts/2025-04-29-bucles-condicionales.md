---
layout: single
title: Bucles y condicionales
excerpt: "..."
date: 2025-04-29
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Python
tags:

---

## ¿Qué es un bucle?

Es una estructura que **repite un bloque de código repetidamente**, esto es muy útil ya que en lugar de escribir el mismo código muchas veces, el bucle lo hace por ti.

## ¿Qué tipos de bucles existen en Python?

- **for**: se usa para repetir cada elemento en una sencuencia, ya sean números o palabras. 

Un ejemplo usando este tipo de bucle sería el siguiente:

![](/assets/images/python/32.png)

![](/assets/images/python/33.png)

En este ejemplo se proporciona una lista con nombres, usando el bucle **for** para que recorra cada nombre de la lista, para que posteriormente printee cada nombre de la lista por separado.

- **while**: este tipo de bucle realiza la misma función que el anterior bucle "for", pero siempre que una condición específica se mantenga como verdadera.

Un ejemplo usando este tipo de bucle sería el siguiente:

![](/assets/images/python/34.png)

En este ejemplo podemos ver que el código tiene una variable "contador" que vale 1, junto con un bucle **While** que printea el valor del contador siempre que el valor de éste sea menor o igual a 10.

![](/assets/images/python/35.png)

El problema está en que como el contador siempre vale 1 y no cambia su valor, el bucle es infinito.

![](/assets/images/python/36.png)

Lo que haríamos para cerrar el bucle sería modificiar el código de esta forma:

![](/assets/images/python/37.png)

![](/assets/images/python/38.png)

En este ejemplo, cada vez que el bucle termina una vuelta, se le suma 1 al valor de "contador", de esta forma llegará un momento en el que el valor de "contador" será igual a 10 y el bucle terminará.


## Bucles anidados

Este tipo de bucles en Python se pueden definir como **bucles que están dentro de otros bucles**.

Un buen ejemplo para este tipo de bucle es el siguiente:

![](/assets/images/python/39.png)
