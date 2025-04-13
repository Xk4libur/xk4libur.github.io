---
layout: single
title: Return - Hack The Box
excerpt: "Lorep ipsum."
date: 2025-04-12
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

![](/assets/images/htb-return/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Windows**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-return/2.png)

Estos son los puertos abiertos en la máquina, entre ellos están el **puerto 80, 88 y el 445**: 

![](/assets/images/htb-return/3.png)

Como el **puerto 80** está **abierto** debe de haber una página web corriendo por detrás, para ver su contenido, copiamos la IP de la máquina víctima en el navegador:

![](/assets/images/htb-return/4.png)

Nada más entrar en la web, veremos esto:

![](/assets/images/htb-return/5.png)

Parece ser un panel de administración para gestionar impresoras, en la parte superior izquierda de la pantalla veremos estas opciones:

![](/assets/images/htb-return/6.png)

Si nos dirigimos a la sección de opciones, veremos que podemos incluir datos como dirección IP, puerto, etc… :

![](/assets/images/htb-return/7.png)

Podrías usar esto para intentar recibir alguna reverse shell para nuestra máquina atacante:

![](/assets/images/htb-return/8.png)

Si antes de actualizar los datos, nos ponemos en escucha por el puerto que incluimos, veremos esto:

![](/assets/images/htb-return/9.png)

Si lo hacemos correctamente, recibiremos estos datos:

![](/assets/images/htb-return/10.png)

Lo que más me llama la atención es "svc-printer" y "1edFg43012!!", parecen ser un nombre de usuario junto con una contraseña.

Con estos datos podemos acceder a la máquina víctima usando **evil-winrm**:

![](/assets/images/htb-return/11.png)

Al acceder podemos ver que somos el usuario "svc-printer":

![](/assets/images/htb-return/12.png)

La flag del usuario no privilegiado se encuentra en la siguiente ruta:

![](/assets/images/htb-return/13.png)

![](/assets/images/htb-return/14.png)

Nuestro objetivo ahora es escalar privilegios para ser el administrador del sistema, para ello podemos ver los privilegios que tenemos siendo el usuario actual:

![](/assets/images/htb-return/15.png)

Parece ser que estamos dentro del grupo "Server Operators":

![](/assets/images/htb-return/16.png)

Podemos buscar en Internet alguna forma de abusar de esto para escalar privilegios:

![](/assets/images/htb-return/17.png)

Encontramos este artícula oficial de Microsoft en el que podremos encontrar información sobre las acciones que puede hacer el grupo "Server Operators":

![](/assets/images/htb-return/18.png)

Los miembros de este grupo pueden realizar diferentes acciones, entre ellas:

- Crear y eliminar recursos compartidos a nivel de red
- Iniciar y detener servicios
- Realizar backups de archivos
- Formatear discos duros de los dispositivos