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

![](/assets/images/htb-good-games/5.png)

Al seleccionar el icono, nos aparecerá esto:

![](/assets/images/htb-good-games/6.png)

Parece ser un panel de login ingresar credenciales para iniciar sesión en la web, esto me huele mucho a **SQL Injection**, así que vamos a iniciar el Burpsuite para proceder con la explotación:

![](/assets/images/htb-good-games/7.png)

Incluimos unas credenciales improvisadas, pero antes de enviarlas, interceptamos con Burpsuite para poder editar la solicitud:

![](/assets/images/htb-good-games/8.png)

![](/assets/images/htb-good-games/9.png)

Aquí podemos ver la solicitud interceptada por Burpsuite, al igual que su contenido como las credenciales incluidas anteriormente:

![](/assets/images/htb-good-games/10.png)

![](/assets/images/htb-good-games/11.png)

En la línea 15 podemos ver el correo y la contraseña que hemos puesto antes, lo que haremos será una inyección sql básica para evitar poder acceder a la web, lo haremos de la siguiente manera:

![](/assets/images/htb-good-games/12.png)

Una explicación sencilla de como funciona esto por detrás es que al pasarle la condición de **1=1**, como esta condición siempre es verdadera y al comentar la contraseña por el uso de los guiones, nos permite ingresar a la web aunque no tengamos las credenciales válidas.

Ahora enviamos la solicitud y nos vamos pa' dentro de la web:

![](/assets/images/htb-good-games/13.png)

![](/assets/images/htb-good-games/14.png)

Una vez dentro de la web, podemos ver que somos el usuario **admin**:

![](/assets/images/htb-good-games/15.png)

No podemos hacer mucho en esta sección de la web, aunque si seleccionamos el icono del engranaje pasará esto:

![](/assets/images/htb-good-games/16.png)

![](/assets/images/htb-good-games/17.png)

La web nos reenvía a otro sitio web al que no podemos acceder de primeras, para poder acceder a esta web, incluimos el nombre del dominio junto con la IP de la máquina víctima en el archivo **/etc/hosts**:

![](/assets/images/htb-good-games/18.png)

Si probamos a lanzar un ping al nombre de dominio incluido en el **/etc/hosts**, podemos ver que tenemos conexión, con lo cual, podemos proceder:

![](/assets/images/htb-good-games/19.png)

Al ingresar dentro del dominio, veremos lo siguiente:

![](/assets/images/htb-good-games/20.png)




