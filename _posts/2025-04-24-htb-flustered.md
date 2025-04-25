---
layout: single
title: Flustered - Hack The Box
excerpt: "Lorem ipsum"
date: 2025-04-24
classes: wide
header:
  teaser:
  teaser_home_page: true
  icon: /assets/images/htb_logo.webp
categories:
  - Hack The Box - Medium
tags:  
---

Empezamos haciendo un **ping** a la máquina víctima para saber si está en línea:

![](/assets/images/htb-flustered/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Linux**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-flustered/2.png)

Entre los puertos abiertos, encontramos el **puerto 80** correspondiente al servicio **http**, además nos muestra un nombre de dominio:

![](/assets/images/htb-flustered/3.png)

Antes de entrar a la web para ver su contenido, vamos a buscar archivos y/o directorios ocultos con **gobuster**:

![](/assets/images/htb-flustered/4.png)

Pues al parecer, no hay nada:

![](/assets/images/htb-flustered/5.png)

Lo único que tenemos de momento es el nombre de dominio, vamos a incluirlo en el archivo **/etc/hosts**, a ver a donde nos lleva:

![](/assets/images/htb-flustered/6.png)

Ahora copiamos el nombre del dominio en el navegador:

![](/assets/images/htb-flustered/7.png)

Esta es la web:

![](/assets/images/htb-flustered/8.png)

La web está guapa, pero no hay nada de contenido que rascar.

Aunque si volvemos a ver el escaneo con nmap encontraremos esto también:

![](/assets/images/htb-flustered/9.png)

Parece ser otro nombre de dominio, vamos a incluirlo en el archivo **/etc/hosts**:

![](/assets/images/htb-flustered/10.png)

Nos lleva a la misma web que antes:

![](/assets/images/htb-flustered/8.png)

De momento no hay nada de la web que se pueda usar a simple vista, aunque si volvemos al escaneo de nmap, veremos este puerto abierto:

![](/assets/images/htb-flustered/12.png)
