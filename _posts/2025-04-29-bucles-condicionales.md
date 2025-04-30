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

Un buen ejemplo para este tipo de bucle es el siguiente, es una lista de números los cuales podemos separar de forma individual usando varios bucles:

![](/assets/images/python/39.png)

Aquí separamos los números de la lista en 3 partes diferentes:

![](/assets/images/python/40.png)

Aunque también podemos separar cada número de cada lista de forma individual:

![](/assets/images/python/41.png)

![](/assets/images/python/42.png)

Si queremos hacer que se vea más atractivo, podemos modificar el código de esta forma:

![](/assets/images/python/43.png)

![](/assets/images/python/44.png)


## Control de flujos en bucles

Existen varias declaraciones que permiten modificar el comportamiento de los bucles:

- **break**: esta declaración detiene el bucle de forma repentina, aunque otras condiciones no se cumplan. Un ejemplo para entender esta declaración es el siguiente.

Creamos un bucle que nos muestre 6 números:

![](/assets/images/python/45.png)

![](/assets/images/python/46.png)

Pero modificamos el código para que cuando el bucle llegue al número 3, se detenga y no muestre más números:

![](/assets/images/python/47.png)

![](/assets/images/python/48.png)

- **continue**: esta declaración ignora una parte del código y pasa a la siguiete vuelta de bucle, en este ejemplo hay un bucle que muestra un rango de números del 1 al 9, al llegar al número 5, no solo muestra, es decir, se salta ese número y sigue mostrando los números restantes:

![](/assets/images/python/49.png)

![](/assets/images/python/50.png)
