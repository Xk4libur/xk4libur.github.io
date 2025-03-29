---
layout: single
title: Good Games - Hack The Box (SIN TERMINAR)
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

Es otro panel de login, en este caso debemos obtener credenciales válidas si queremos seguir.

Lo que haremos para proseguir, será la solicitud que usamos antes, pero la usaremos en la opción del **Repeater** de **Burp Suite** para poder ver el código de la web y ver los cambios que hay mientras avanzamos:

![](/assets/images/htb-good-games/21.png)

Si intentamos ver el nombre de la base de datos por medio de este comando, podremos ver que: 

![](/assets/images/htb-good-games/22.png)

No ocurre nada, así que vamos a filtrar por el número de columnas que tiene la base de datos a ver si conseguimos algo de información sobre los usuarios:

![](/assets/images/htb-good-games/25.png)

Si en la barra inferior de la derecha añadimos la palabra "welcome", podremos saber cuando hay una cambio significativo en la web:

![](/assets/images/htb-good-games/26.png)

De hecho, podemos ver que ya tenemos un match, ya que nos aparece este detalle:

![](/assets/images/htb-good-games/27.png)

Esto nos dá el nombre de la base de datos ‘main’, como ya sabemos el nombre de la base de datos, ya podemos empezar a sacarle los datos que queramos, empezando por la cantidad de tablas que tiene:

![](/assets/images/htb-good-games/28.png)

![](/assets/images/htb-good-games/29.png)

Nos devuelve muchas tablas en un formato que no es cómodo de leer, pero lo importante es lo que se encuentra al final de todo esto:

![](/assets/images/htb-good-games/30.png)

Hay una tabla llamada **user**, y es de ahí de donde sacaremos todos los datos:

![](/assets/images/htb-good-games/31.png)

Aunque no nos devuelve los valores que queremos, si que nos dice que podemos encontrar en la tabla:

![](/assets/images/htb-good-games/32.png)


