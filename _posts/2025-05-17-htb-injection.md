---
layout: single
title: Injection - Hack The Box
excerpt: "Lorem ipsum."
date: 2025-05-17
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
 
![](/assets/images/htb-inject/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Linux**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-inject/2.png)

Podemos ver que solo hay 2 puertos abiertos, el **22** y el **8080**. 

Vamos a copiar la IP de la máquina en el navegador para ver si hay alguna web por detrás:

![](/assets/images/htb-inject/3.png)

Al parecer no hay nada de información útil:

![](/assets/images/htb-inject/4.png)

Vamos a copiar el puerto 8080 de la máquina víctima junto con la IP, a ver si encontramos algo:

![](/assets/images/htb-inject/5.png)

![](/assets/images/htb-inject/6.png)

Hay una web por detrás, parecer ser algún servicio de almacenamiento de archivos en la nube, en la parte superior podremos ver esta barra de opciones:

![](/assets/images/htb-inject/7.png)

No hay nada de información útil a plena vista, así que vamos a buscar archivos y/o directorios ocultos con gobuster:

![](/assets/images/htb-inject/8.png)

Entre los directorios que hay, me llama la atención el “**/register**”, vamos a incluirlo en la URL para ver que contiene:

![](/assets/images/htb-inject/9.png)

Parece ser que esta sección de la web, esta todavía en fase de desarrollo:

![](/assets/images/htb-inject/10.png)

Vamos a dirigirnos al directorio “**/blogs**”:

![](/assets/images/htb-inject/11.png)

Tampoco hay nada que nos pueda interesar:

![](/assets/images/htb-inject/12.png)

Vamos al directorio “**/uploads**”, es el único interesante que queda en la máquina:

![](/assets/images/htb-inject/13.png)

En la esquina superior derecha, podremos ver esta opción:

![](/assets/images/htb-inject/14.png)

Al seleccionar la opción, nos aparece una barra para subir archivos a la web:

![](/assets/images/htb-inject/15.png)

Vamos a tratar de subir un archivo de texto solo como una prueba:

![](/assets/images/htb-inject/16.png)

![](/assets/images/htb-inject/17.png)

La web solo acepta archivos de que sean imágenes:

![](/assets/images/htb-inject/18.png)

Vamos a iniciar el Burpsuite para controlar mejor las peticiones: 

![](/assets/images/htb-inject/19.png)

La peticición HTTP que tengamos, la mandamos al "repeater":

![](/assets/images/htb-inject/20.png)

Desde aquí, podemos ver el nombre del archivo que subamos:

![](/assets/images/htb-inject/21.png)

Vamos a probar a cambiar la extensión del archivo desde texto a imagen:

![](/assets/images/htb-inject/22.png)

En este caso, si que nos permite subir el archivo, y además podremos ver esto:

![](/assets/images/htb-inject/23.png)

Esto me suena mucho a un **Local File Inclusion**, de hecho en la propia máquina aparece como uno de los temas que se tratan:

![](/assets/images/htb-inject/24.png)

Vamos a hacer una petición con CURL directamente a la ruta donde se encuentra el archivo que subimos anteriormente, para ver si podemos encontrar algo que nos sirva:

![](/assets/images/htb-inject/25.png)

