---
layout: single
title: Validation - Hack The Box
excerpt: "Una buena máquina para practicar con la SQL Injection usando Burpsuite, además de enumerar archivos con gobuster."
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

Para saber en qué base de datos estamos actualmente, vamos a probar con esta sql injection básica:

![](/assets/images/htb-validation/12.png)

Enviamos la solicitud:

![](/assets/images/htb-validation/13.png)

Podemos ver que estamos dentro de la base de datos "Registration":

![](/assets/images/htb-validation/14.png)

Seguramente esta base de datos es usada para almacenar la información, pero puede ser que la web tenga más bases de datos a parte de esta, así que vamos a probar con esta modificación de la sqli anterior:

![](/assets/images/htb-validation/15.png)

Nos aparecen todas las bases de datos que tiene la web por detrás:

![](/assets/images/htb-validation/16.png)

Nos veo nada importante por aquí, así que vamos a sacar toda la información que tiene la base de datos “Registration”, como toda la información de los usuarios se guarda ahí, al igual podemos encontrar datos interesantes de otros usuarios:

![](/assets/images/htb-validation/17.png)

Parece ser que no hay otros usuarios más del que creamos anteriormente con el nombre de “xk4libur”:

![](/assets/images/htb-validation/18.png)

Como en la web no podemos sacar más datos, vamos a probar a buscar directorios y/o archivos ocultos con **gobuster**:

![](/assets/images/htb-validation/20.png)

No encontramos nada si miramos de forma general, vamos a probar a buscar archivos con extensión **.php** y **.txt**:

![](/assets/images/htb-validation/21.png)

Podemos ver que hay un archivo con extensión **.php**, vamos a ver que contiene:

![](/assets/images/htb-validation/24.png)

Pues no hay nada, de lujo.

Podemos intentar subir algún archivo que nos permita hacer un RCE y así poder obtener una reverse shell, lo podemos hacer con esta modificación en la solicitud:

![](/assets/images/htb-validation/25.png)

Lo que estamos haciendo es subir un archivo llamado **pwned.php** que nos permita ejecutar comandos de forma remota en la web usando la URL.

Antes de lanzar la solicitud, desactivamos la interceptación de Burpsuite, ya que ya no es necesaria:

![](/assets/images/htb-validation/26.png)

Una vez subido el archivo, vamos a acceder a él:

![](/assets/images/htb-validation/27.png)

![](/assets/images/htb-validation/28.png)

Podemos ejecutar comandos directamente en el servidor usando la URL de la web:

![](/assets/images/htb-validation/29.png)

Si ejecutamos el comando **whoami**, veremos que somos el usuario "www-data":

![](/assets/images/htb-validation/30.png)

Para ganar acceso a la máquina, pondremos el código de una reverse shell pero de tal forma que esté en formato de URL, esto lo haremos con Burpsuite.

Nos dirigimos a esta sección del Burpsuite:

![](/assets/images/htb-validation/31.png)

Incluimos este código de reverse shell:

![](/assets/images/htb-validation/32.png)

Encodeamos el código como URL:

![](/assets/images/htb-validation/33.png)

![](/assets/images/htb-validation/34.png)

Nos ponemos en escucha por el puerto que hemos incluido en el código y copiamos el código de la URL en la barra de búsqueda:

![](/assets/images/htb-validation/35.png)

![](/assets/images/htb-validation/36.png)

Ya estamos dentro de la máquina:

![](/assets/images/htb-validation/37.png)

Realizamos un tratamiento de la tty para que la terminal no explote:

![](/assets/images/htb-validation/38.png)

![](/assets/images/htb-validation/40.png)

La flag del usuario no privilegiado se encuentra en la siguiente ruta: "/home/htb":

![](/assets/images/htb-validation/43.png)

Tras investigar los directorios de la máquina no se encontró nada de información útil, sin embargo, si investigamos la siguiente ruta “/var/www/html”, encontraremos esto:

![](/assets/images/htb-validation/45.png)

Podemos ver que hay una contraseña en texto plano, vamos a intentar usarla para escalar al usuario administrador:

![](/assets/images/htb-validation/46.png)

![](/assets/images/htb-validation/47.png)

Ahora solo vamos al directorio del usuario root, y buscamos la flag:

![](/assets/images/htb-validation/48.png)


## ⚡ MACHINE PWNED ⚡

![](/assets/images/htb-validation/49.png)
