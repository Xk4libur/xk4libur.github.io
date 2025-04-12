---
layout: single
title: Validation - Hack The Box
excerpt: "Lorep ipsum"
date: 2025-04-07
classes: wide
header:
  teaser:
  teaser_home_page: true
  icon: /assets/images/htb_logo.webp
categories:
  - Hack The Box - Easy
tags:  
---

Empezamos haciendo un **ping** a la máquina víctima para saber si está en línea:

![](/assets/images/htb-validation/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Linux**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-validation/2.png)

Podemos ver que el **puerto 80** que corresponde al servicio **http** está abierto, seguramente hay una página web corriendo por detrás.

Para comprobarlo, podemos copiar la IP de la máquina en el navegador:

![](/assets/images/htb-validation/3.png)

![](/assets/images/htb-validation/4.png)

Podemos ver que la web tiene un panel en el que podemos incluir algún nombre y también elegir un país, vamos a probar con este nombre:

![](/assets/images/htb-validation/5.png)

Nos aparecerá esto:

![](/assets/images/htb-validation/6.png)

Si podemos añadir nombres de usuario, tiene que haber una base de datos dentro de la web con nombres de usuario y contraseñas. 

Asi que para sacar esa información, usaremos Burpsuite para interceptar peticiones HTTP desde el navegador hasta el servidor que contiene la web:

![](/assets/images/htb-validation/8.png)

Activamos la interceptación:

![](/assets/images/htb-validation/9.png)

Lanzamos una petición a la web poniendo cualquier nombre de usuario:

![](/assets/images/htb-validation/10.png)

Podemos ver tanto la petición, como la información que contiene en cuanto a nombre de usuario:

![](/assets/images/htb-validation/11.png)
