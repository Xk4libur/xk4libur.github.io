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

Podemos ver que hay **2 puertos abiertos**, el **22** y el **8080**, en esta máquina en concreto, el puerto 8080 tiene el servicio http corriendo, así que seguramente hay una página web ejecutándose por detrás.

Si copiamos la IP de la máquina víctima en el navegador, veremos esto:

![](/assets/images/htb-builder/3.png)

![](/assets/images/htb-builder/4.png)

**Jenkins** es un servidor de automatización de código abierto hecho en Java que permite la automatización de tareas de compilación, pruebas y despliegue, además de facilitar el desarrollo de software.

Si miramos en la esquina inferior derecha, veremos la versión de este servicio:

![](/assets/images/htb-builder/5.png)

Saber la versión del servicio es muy importante, ya que podemos buscar exploits para esta versión en específico:

![](/assets/images/htb-builder/11.png)

Mientras buscamos el exploit podemos ver que la vulnerabilidad que tiene la máquina es que podemos leer el contenido de los archivos que tiene la máquina en local, lo cual nos permite acceder a información confidencial:

![](/assets/images/htb-builder/15.png)

Elegimos este repositorio para proceder:

![](/assets/images/htb-builder/12.png)

Podemos ver que el exploit es un archivo en Python:

![](/assets/images/htb-builder/13.png)

El comando para poder usar el exploit es el siguiente:

![](/assets/images/htb-builder/14.png)

Nos clonamos el repositorio:

![](/assets/images/htb-builder/16.png)

Ponemos la instrucción para hacer funcionar el comando, en este intento intentaremos leer el archivo **/etc/passwd**:

![](/assets/images/htb-builder/17.png)

Al primer intento podemos ver que no rula:

![](/assets/images/htb-builder/18.png)

Por algún motivo el script falla, así que lo mandamos pa’ la puñeta:

![](/assets/images/htb-builder/19.png)

Podemmos elegir este otro repositorio:

![](/assets/images/htb-builder/21.png)

Esta es la forma en la que ejecutamos el exploit:

![](/assets/images/htb-builder/22.png)

Y esta vez, si que rula:

![](/assets/images/htb-builder/23.png)

Lo curioso de este repositorio es que en sus instrucciones podemos ver algunas rutas donde se supone que podemos leer el contenido de dichos archivos:

![](/assets/images/htb-builder/24.png)

Vamos a intentar leer la siguiente ruta **/var/jenkins_home/users/users.xml**:

![](/assets/images/htb-builder/25.png)

Conseguimos leer el contenido del archivo y podemos ver que hay un usuario llamado **jennifer**, acompañado de una serie de caracteres que nos pueden ser de utilidad para obtener la contraseña:

![](/assets/images/htb-builder/26.png)

![](/assets/images/htb-builder/27.png)

Si intentamos leer el contenido de esta ruta, veremos que:

![](/assets/images/htb-builder/28.png)

Hay un hash muy grande que resulta ser el hash de la contraseña del usuario no privilegiado:

![](/assets/images/htb-builder/29.png)

Para sacar la contraseña, nos copiamos el hash en un archivo de texto y lo pasamos por la herramienta de **John The Ripper**:

![](/assets/images/htb-builder/30.png)

![](/assets/images/htb-builder/31.png)

Si nos volvemos a la web de Jenkins, podremos iniciar sesión con estas credenciales:

![](/assets/images/htb-builder/32.png)

Al investigar la web, podemos acceder a varias rutas de la misma, entre ellas la siguiente: 

![](/assets/images/htb-builder/33.png)

Podemos acceder a una consola que nos permite ejecutar instrucciones:

![](/assets/images/htb-builder/34.png)

![](/assets/images/htb-builder/35.png)

![](/assets/images/htb-builder/36.png)

Si intentamos poner una suma para que la terminal interprete el código y nos devuelva el resultado, veremos que, nos lo interpreta:

![](/assets/images/htb-builder/37.png)

![](/assets/images/htb-builder/38.png)


