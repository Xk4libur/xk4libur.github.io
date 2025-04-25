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

Entre los puertos abiertos de la máquina, se encuentra el **puerto 80**:

![](/assets/images/htb-flustered/3.png)

Podemos ver que nos aparece un nombre de dominio "**steampunk-era.htb**", junto con un mensaje de "**Coming soon**", puede ser que la web esté en desarrollo o en mantenimiento.

Si copiamos la IP de la máquina víctima en el navegador, veremos esto:

![](/assets/images/htb-flustered/4.png)

![](/assets/images/htb-flustered/5.png)

La web está guapa, pero no hay nada de información que rascar de aquí. 