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

El **shebang** (#!) es una línea especial que se coloca al inicio de un script en Python para indicar al sistema operativo con intérprete se debe ejecutar el script. 

Lo ideal es escribir el shebang de esta forma: 

**#!/usr/bin/env python3**

Un ejemplo del shebang en un archivo sería el siguiente: 

```python3
#!/usr/bin/env python3
print("Hola, hacker!")
```
Si no incluyésemos el shebang en el código, no se podría ejecutar como si fuera un script normal, es decir, no podría ejecutar con este comando: 

```bash
./script.py
```
Tendría que ser solo con este comando:

```bash
python3 script.py
```
## ¿Qué son los convenios de Python?

Los convenios de Python son una serie de **reglas** que los programadores pueden seguir para **escribir código** Python de forma **limpia**, **legible y fácilmente mantenible** a largo plazo. 

No es obligatorio seguir estas convenciones al toque, pero ayudan a que el código sea más profesional y fácilmente entendible para otros programadores. 

Existen muchos convenios de Python, pero los más importantes son: 

- **PEP 8**: define cómo escribir código limpio y legible en Python.
- **PEP 20**: define los principios filosóficos de Python.
- **PEP 257**: define cómo escribir comentarios y documentos en Python usando las comillas triples (""" """).

## ¿Convenio de nomenclaturas de Python?

Cuando se escribe código en Python, es importante **seguir un estándar** de nombres para que sepamos diferenciar bien que es cada cosa. 
En Python existen diferentes formas para **nombrar variables, funciones, clases y constantes**. 

- **snake_case**: se usa en nombres de variables y funciones, este estándar se usa con todo en minúsculas y con guiones bajos 

**Código de ejemplo de "snake_case"**:

```bash
nombre_usuario = "xK4libur"  # Variable
def obtener_datos():  # Función
    pass
```

