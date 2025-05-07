---
layout: single
title:  Listas en Python
excerpt: "Lorep ipsum"
date: 2025-05-01
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Python
tags:

---

## ¿Qué son las listas?

Las **listas** son **estructuras de datos** que se usan para almacenar elementos de forma ordenada. Estos elementos se pueden modificar, además las listas permiten añadir o quitar elementos, lo que evita que los elementos sean fijos.

Un ejemplo de una lista es el siguiente:

![](/assets/images/python/76.png)

En caso de que las listas tengan elementos desordenados, hay una forma de poder ver el resultado de la lista de forma ordenada:

![](/assets/images/python/77.png)

Es tan sencillo como añadir la función de “**sort()**” a la lista para que al imprimir la lista por pantalla, los elementos aparezcan ordenados.

![](/assets/images/python/78.png)

Aquí ya se ven los números ordenados correctamente.

## Características de las listas en Python

Las listas también tienen ciertas características que las hacen más útiles, entre ellas: 

### Almacenar datos de diferentes tipos dentro de una misma lista:
<br>
![](/assets/images/python/79.png)

![](/assets/images/python/80.png)

### Acceder a elementos específicos de la lista usando su índice, o también llamado indexar lista:
<br>
Aquí tenemos una lista de nombres como ejemplo:

![](/assets/images/python/81.png)

Si queremos ver el primer elemento de la lista, ponemos lo siguiente:

![](/assets/images/python/82.png)

El resultado es el siguiente:

![](/assets/images/python/83.png)

También podemos sacar el último elemento de la lista, en este caso NO hay que poner el número del índice del último elemento de la lista, ya que en caso de que la lista cambie, el último elemento también cambiará. 

Para asegurarnos de que sacamos siempre el último elemento de la lista, hacemos lo siguiente:

![](/assets/images/python/84.png)

![](/assets/images/python/85.png)

También es posible sacar varios elementos de una lista al mismo tiempo, en este caso se sacarán los **3 primeros elementos**:

