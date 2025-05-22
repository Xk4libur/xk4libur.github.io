---
layout: single
title: Tuplas en Python
excerpt: "Lorem ipsum"
date: 2025-05-22
classes: wide
header:
  teaser:
  teaser_home_page: true
  icon: /assets/images/python_logo.webp
categories:
  - Python
tags:  
---

Las tuplas son colecciones de elementos ordenados que, una vez son creadas, ya no pueden ser modificadas. Esta característica las hace diferentes a las listas, ya que las tuplas mantienen los valores de los elementos de forma constante a largo plazo.

Las tuplas son usadas en situaciones donde los elementos no deben ser modificados o no tienen sentido modificarlos.


## ¿Cuáles son las características de las tuplas?

### Inmutabilidad 

Los datos de una tupla no se pueden cambiar, añadir ni eliminar.

En este ejemplo se ha creado una tupla con una secuencia de números y se intenta sustituir el primer número de la tupla por otro diferente, como en este caso es una tupla, el cambio no se puede realizar correctamente:

![](/assets/images/python/92.png)

![](/assets/images/python/93.png)

El error que aparece significa que la tupla no soporta que se le asigne un nuevo elemento.

### Indexación 

Los elementos pueden ser accesibles desde su índice.

En este ejemplo se ha creado una tupla con una secuencia de números y se muestran los números de la tupla basados en su índice en cuanto a su posición dentro de la tupla:

![](/assets/images/python/94.png)

![](/assets/images/python/95.png)

### Heterogeneidad 

Una tupla puede tener elementos de diferentes tipos, ya sean **números**, **texto**, **listas** o **incluso** otras tuplas. 

En este ejemplo se ha creado una tupla que contiene elementos de diferentes tipos:

![](/assets/images/python/96.png)

![](/assets/images/python/97.png)

Aprovechando que una tupla puede contener diferentes tipos de elemntos, podemos combinarla con una bucle '**for**' para que nos muestre cada tipo de valor de cada elemento de la tupla:

![](/assets/images/python/98.png)

![](/assets/images/python/99.png)
