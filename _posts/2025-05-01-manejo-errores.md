---
layout: single
title:  Manejo de errores y excepiones
excerpt: "En todos los lenguajes de programación pueden aparecer errores en cualquier momento al ejecutar un programa, y es importante saber cómo tratarlos para controlar el flujo del programa para que no colapse del todo y pueda tener una salida controlada."
date: 2025-05-01
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Python
tags:

---

## ¿Por qué ocurren errores en Python?

Los errores puede ocurrir por infinidad de razones: errores en el própio código, datos de entrada incorrectos, problemas de conectividad a nivel de red, archivos que no existen, etc... .

Aunque Python detiene la ejecución del programa y muestra un mensaje de excepción, no es deseable en aplicaciones reales que usen muchos usuarios, ya que se pueden presentar situaciones como:

- La ejecución se interrumpe de golpe con datos en procesamiento

- Se pierden datos importantes o se corrompen procesos sin guardar o en plena ejecución

- El usuario final ve un error confuso y piensa que ha sido hackeado por xk4libur


## ¿Que ayuda tenemos de parte de Python?

Para solucionar todo esto, Python nos ofrece una estructura muy poderosa para manejar expeciones, llamada el bloque **try-except**. 

Un ejemplo para entender el manejo de errores en Python es el siguiente:

![](/assets/images/python/70.png)

En el programa se intenta dividir 5 entre 0, todo sabemos que eso dará error:

![](/assets/images/python/71.png)

Python nos dice el error es de tipo **ZeroDivisionError**, es decir, error por dividir entre 0.

Pero si ahora hacemos esta modificación el código:

![](/assets/images/python/72.png)

Ahora hemos dicho que pruebe a hacer la operatoria y en caso de ocurra de nuevo el mimso error que antes, mostrará un mensaje por consola:

![](/assets/images/python/73.png)
