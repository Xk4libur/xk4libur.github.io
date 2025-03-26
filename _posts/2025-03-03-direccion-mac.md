---
layout: single
title: Direcciones MAC
date: 2025-03-05
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Dirección MAC
tags:
---
Una **dirección MAC** tambien llamada com (Media Access Control) es un identificador "único" que se le asigna una tarjeta de red de un dispositivo. Es como el DNI de una tarjeta de red.

## Ejemplo visual de una dirección MAC

![](/assets/images/direccion-mac/1.png)


Una dirección MAC se representa en formato **hexadecimal** y se divide en 6 bloques de 2 caracteres, cada uno de estos bloques separados por 2 puntos (:).

Los **3 primeros bloques** forman el OUI (Organizationally Unique Identifier):

![](/assets/images/direccion-mac/2.png)

Los **3 últimos bloques** forman el NIC (Network Interface Controller).

![](/assets/images/direccion-mac/3.png)

El **OUI** de la dirección MAC representa al fabricante de dicha tarjeta de red, mientras que el **NIC** representa el modelo de la tarjeta de red.

## "¿Realmente la dirección MAC es un identificador 'único'?"

Realmente la dirección MAC **no** es un identificador único debido a que existen herramientas como **macchanger** que permiten cambiar la MAC de una tarjeta de red para ciertos casos.

Algunos ejemplos son: 

- **Anonimato**: para ocultar la MAC real del dispositivo en redes públicas y evitar ser rastreado.
- **Pentesting**: para realizar pruebas de seguridad y auditorías Wi-Fi. 
