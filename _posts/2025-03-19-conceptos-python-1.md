---
layout: single
title: Conceptos básicos de Python - Parte 1 (SIN TERMINAR)
excerpt: "Lorem ipsum."
date: 2025-03-19
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - python
tags:
  - python
---

## El intérprete de Python

El intérprete de Python es el **corazón del lenguaje** de programación de Python, es el motor que ejecuta el código proporcionado por los programadores. En otras palabras es el programa que lee y ejecuta el código Python en tiempo real.

![](/assets/images/python/1.png)

Las funciones principales del intérprete de Python son las siguientes: 

- **Ejecución de código**: el intérprete ejecuta el código escrito línea por línea, permitiendo a los programadores probar fragmentos de código de forma más sencilla. 

- **Modo interactivo**: el intérprete puede usarse en modo interactivo, lo que permite un entorno ideal para que los principiantes puedan aprender y explorar el lenguaje, este modo es ideal para probar comandos sin tener que escribir programas completos. Este modo permite ejecutar comandos tan rápido como se terminen de escribir. 

- **Modo de script**: este modo es usado por los programadores más experimentados, se usa para desarrollar programas complejos, en este modo los programas son guardados en extension "**.py**".

## Ejemplos sencillos de operaciones básicas en el intérprete de Python

![](/assets/images/python/2.png)

![](/assets/images/python/3.png)

![](/assets/images/python/4.png)

![](/assets/images/python/5.png)

## ¿Qué es el shebang en Python?

El **shebang** (#!) es una línea especial que se coloca al inicio de un script en Python para indicar el intérprete con el que se debe ejecutar el script. 

Un ejemplo del shebang sería el siguiente: 

```python3
#!/usr/bin/env python3
print("Hola, hacker!")
```
Si no incluyésemos el shebang en el código, no se podría ejecutar como si fuera un script normal, es decir, no podría ejecutar con este comando: 

```bash
./script.py
```
Tendría que ser solo con este comando:

```python3
python3 script.py
```


