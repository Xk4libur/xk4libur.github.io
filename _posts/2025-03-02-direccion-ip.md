---
layout: single
title: Direccion IP (sin terminar)
date: 1999-01-01
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - slae
  - infosec
tags:
  - slae
  - assembly
  - tcp bind shellcode
---
Una **dirección IP** es un **identificador númerico único** asignado a un dispositivo al conectarse a una red. Este dispositivo puede ser una computadora, una tableta, un router, un servidor, entre otros.

Un ejemplo de una dirección ip puede ser el siguiente:

![](/assets/images/direccion-ip/1.png)

En mi caso, tengo un entorno con BSPWM que muestra constantemente mi IP pública. Sin embargo, si no conocemos nuestra dirección IP, podemos obtenerla fácilmente ejecutando el siguiente comando en la terminal:

![](/assets/images/direccion-ip/2.png)

Existen dos tipos de direcciones IP: **IPv4** e **IPv6**. A nivel informático, una dirección IP no es más que una secuencia de bits. Las direcciones **IPv4** tienen una longitud de **32 bits**, mientras que las direcciones **IPv6** cuentan con **128 bits**, lo que permite una mayor cantidad de combinaciones y, por ende, más direcciones disponibles.

Si queremos visualizar una dirección IP en formato binario, podemos hacerlo ejecutando los siguientes comandos en la terminal:

![](/assets/images/direccion-ip/3.png)

Una manera de calcular la cantidad máxima de direcciones IPv4 e IPv6 posibles es ejecutando el siguiente comando en la terminal:

- Cantidad máxima de direcciones IPv4:

![](/assets/images/direccion-ip/4.png)

- Cantidad máxima de direcciones IPv6:

![](/assets/images/direccion-ip/5.png)

## Ejemplo visual