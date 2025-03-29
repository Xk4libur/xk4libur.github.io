---
layout: single
title: Good Games - Hack The Box
excerpt: "Lorep ipsum."
date: 2025-03-29
classes: wide
header:
  teaser:
  teaser_home_page: true
  icon: /assets/images/htb_logo.webp
categories:
  - Hack The Box
tags:  
  - máquinas fáciles
  - sql injection
---

Empezamos haciendo un **ping** a la máquina víctima para saber si está en línea:
 
![](/assets/images/htb-good-games/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Linux**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-good-games/2.png)

Al parecer solo hay un puerto abierto, es el **puerto 80** que corresponde al servicio **http**, es decir, hay una página web corriendo por detrás de la máquina.

Para ver el contenido de la web, copiamos la IP de la máquina víctima en el navegador:

![](/assets/images/htb-good-games/3.png)

![](/assets/images/htb-good-games/4.png)

Parece ser que el contenido de la web está relacionado con videojuegos, y algo que me llama la atención es que hay un logo con forma de usuario en la parte superior derecha:


