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

Vamos a probar a buscar archivos y/o directorios ocultos en la web, puede ser que hayan archivo dentro que nos sean de utilidad:

![](/assets/images/htb-flustered/6.png)

Pues no hay nada, de lujo:

![](/assets/images/htb-flustered/7.png)

Si nos volvemos al escaneo de nmap, podremos ver este nombre de dominio que vimos anteriormente:

![](/assets/images/htb-flustered/8.png)

Si hacemos un **ping** a este nombre de dominio, veremos que no tenemos conexión con el mismo:

![](/assets/images/htb-flustered/9.png)

La solución es sencilla, simplemente añadimos la IP junto con el nombre de dominio al archivo **/etc/hosts**:

![](/assets/images/htb-flustered/10.png)

Ahora tenemos conexión con el dominio:

![](/assets/images/htb-flustered/11.png)

Si ponemos el dominio en el navegador, nos llevará aquí:

![](/assets/images/htb-flustered/12.png)

La misma web que antes:

![](/assets/images/htb-flustered/13.png)

Sin embargo, en el escaneo de nmap había otro puerto que tenía un dominio diferente:

![](/assets/images/htb-flustered/14.png)

Al igual que antes, no tenemos conexión:

![](/assets/images/htb-flustered/15.png)

Añadimos este nuevo dominio al archivo **/etc/hosts**:

![](/assets/images/htb-flustered/16.png)

Si vemos el contenido del dominio, veremos que:

![](/assets/images/htb-flustered/17.png)

Literalmente, la misma web otra vez:

![](/assets/images/htb-flustered/18.png)

Si volvemos a ver el escaneo de nmap, veremos que hay un puerto que me llama la atención, el **3128** que tiene algo llamado **squid proxy** corriendo por detrás:

![](/assets/images/htb-flustered/19.png)

## ¿Qué es un squid proxy?

Es un servidor que actúa como intermediario entre el cliente y el servidor web de destino, este tipo de servidores tienen varias funciones, entre ellas: 

- Cachear página web realizando copias de las mismas para ahorrar ancho de banda y acelerar el acceso
- Bloquear sitios web
- Monitorear el tráfico de red