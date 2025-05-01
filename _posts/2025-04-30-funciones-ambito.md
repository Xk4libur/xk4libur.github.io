---
layout: single
title: 
excerpt: "..."
date: 2025-04-30
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Python
tags:

---

## ¿Qué son las funciones en Python?

Una función es un bloque de código reutilizable diseñado para hacer una tarea específica. En Python se definen usando la palabra "**def**".

En este ejemplo se puede ver una función "**def**" que, al ser llamada, imprime un mensaje por consola:

![](/assets/images/python/58.png)

![](/assets/images/python/59.png)

También se pueden usar para sumar números y devolver el resultado:

![](/assets/images/python/60.png)

![](/assets/images/python/61.png)

## ¿Qué son las funciones "lambda" anónimas en Python?

Las **funciones lambda** son una forma rápida y sencilla de escribir funciones simples y pequeñas. Estas funciones no tienen nombre (de ahí lo de ***anónimas***) y se usan cuando se necesita una función simple en una sola línea, ahorrandose de escribir todo el bloque de código para una función normal.

Un ejemplo de este tipo de función sería el siguiente:

![](/assets/images/python/62.png)

![](/assets/images/python/63.png)

La función lambda contiene unas funciones de orden superior que ayudan a que el código sea más simple y eficiente, estas funciones son ideales para trabajar con listas. Estas funciones son:

- **map**: aplica una función a cada elemento de una lista.

En el siguiente ejemplo, se muestra un programa que toma los números de una lista y devuelve los números al cuadrado de los números de la lista:

![](/assets/images/python/64.png)

![](/assets/images/python/65.png)


- **filter**: filtra elementos que cumplen una condición

En el siguiente ejemplo, se muestra un programa que toma los números de una lista y devuelve los números que son pares:

![](/assets/images/python/66.png)

![](/assets/images/python/67.png)

- **sorted**: ordena elementos usando una función personalizada

En el siguiente ejemplo, se muestra un programa que toma las palabras de una lista y las ordena en cuanto a cantidad de letras, de menor a mayor:

![](/assets/images/python/68.png)

![](/assets/images/python/69.png)
