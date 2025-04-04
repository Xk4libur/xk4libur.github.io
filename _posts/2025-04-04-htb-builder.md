---
layout: single
title: Builder - Hack The Box (SIN TERMINAR)
excerpt: "Lorep ipsum."
date: 2025-04-04
classes: wide
header:
  teaser:
  teaser_home_page: true
  icon: /assets/images/htb_logo.webp
categories:
  - Hack The Box
tags:  
  - Medium machines
  - Weak credentials
---

Empezamos haciendo un **ping** a la máquina víctima para saber si está en línea:

![](/assets/images/htb-builder/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Linux**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-builder/2.png)