---
layout: single
title: Cicada - Hack The Box (SIN TERMINAR) 2.0
excerpt: "Lorep ipsum."
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

![](/assets/images/htb-cicada/1.png)

Podemos ver que hay conexión con la máquina víctima y por el número del **TTL**, podemos definir que es una **máquina Windows**. 

Ahora que ya sabemos que tenemos conexión pasamos a escanear los puertos abiertos de la máquina:

![](/assets/images/htb-cicada/2.png)

Podemos ver que hay muchos puertos abiertos, de todos ellos destaca el **puerto 5985** que está ejecutando el servicio **http**, así que seguramente hay una página web corriendo por detrás.

Copiamos la IP de la máquina víctima en el navegador junto con el puerto específico:

![](/assets/images/htb-cicada/3.png)

Parece ser que no hay nada que ver en la web.

![](/assets/images/htb-cicada/4.png)

Algo que me llamó la atención es que el **puerto 445** está abierto, además de que en otros puertos abiertos se registró “Active Directory”, es decir, que esta máquina seguramente es un servidor Windows.

![](/assets/images/htb-cicada/5.png)

Lo que podemos hacer para estar seguros de que es un servidor, es usar el comando **netexec** para obtener información sobre la máquina víctima:

![](/assets/images/htb-cicada/6.png)

![](/assets/images/htb-cicada/7.png)

No solo confirmamos que es un servidor, sino que obtenemos el nombre del dominio del servidor “cicada.htb”.

Lo que podemos hacer ahora es intentar obtener nombres de usuario que estén dentro del servidor, para eso usaremos “kerbrute”, el cual lo podemos descargar de este repositorio:

![](/assets/images/htb-cicada/8.png)

Una vez descargado, usaremos esta herramienta junto con una lista que contiene muchos millones de nombres de usuario para ver cuantos nombres de usuario podemos obtener del servidor:

![](/assets/images/htb-cicada/9.png)

![](/assets/images/htb-cicada/10.png)

Podemos ver algunos nombres de usuario del servidor, pero necesitamos obtener más información, lo que podemos hacer es listar el contenido de recursos compartidos a nivel de red del servidor:

![](/assets/images/htb-cicada/11.png)

Hay un recurso que me llama la atención, es el recurso “HR”, que parece algo relacionado con Recursos Humanos:

![](/assets/images/htb-cicada/13.png)

Podemos ver que hay un archivo de texto llamado "Notice from HR.txt", lo que haremos será descargar este archivo:

![](/assets/images/htb-cicada/14.png)

Dentro del archivo, podemos ver una contraseña:

![](/assets/images/htb-cicada/15.png)

![](/assets/images/htb-cicada/15-1.png)

Para poder seguir necesitamos más nombres de usuarios, podemos usar la herramienta “netexec” para obtener nombres que tengan el ID de usuarios:

![](/assets/images/htb-cicada/16.png)

Obtenemos la siguiente cantidad de nombres de usuarios disponibles:

![](/assets/images/htb-cicada/17.png)

Lo que haremos será usar esta lista de nombres de usuario junto con la contraseña obtenida para ver a qué usuario corresponde la contraseña:

![](/assets/images/htb-cicada/18.png)

![](/assets/images/htb-cicada/19.png)

Aunque hemos conseguido solo este nombre de usuario como válido, algo me dice que hay más nombres de usuario con esta misma contraseña, para poder verlos, usamos el mismo comando pero con este parámetro al final del mismo “--continue-on-success”:

![](/assets/images/htb-cicada/20.png)

![](/assets/images/htb-cicada/21.png)

Al parecer sí que había otro nombre de usuario compatible con la contraseña, es el usuario “michael.wrightson”.

Con esta información disponible, vamos a ver los recursos compartidos del servidor a los cuales puede acceder este usuario:

![](/assets/images/htb-cicada/22.png)

![](/assets/images/htb-cicada/23.png)

Podemos ver los recursos compartidos a los cuales este usuario tiene acceso, pero no encuentro nada interesante.

Vamos a probar a volver a listar nombres de usuario a ver si encontramos algo interesante:

![](/assets/images/htb-cicada/24.png)

Dentro del output del comando, encontramos esto:

![](/assets/images/htb-cicada/25.png)

Parece ser que el usuario “david.ourelious” no es tán listo como pensaba y ha puesto su contraseña en texto plano, otro usuario al cual podemos acceder y ver a qué recursos tiene acceso.

Aunque antes podemos verificar si la contraseña es real, y no es una trolleada del usuario:

![](/assets/images/htb-cicada/26.png)

La contraseña es real y funciona, así que vamos a ver los recursos compartidos a nivel de red a los cuales este usuario tiene acceso:

![](/assets/images/htb-cicada/27.png)

![](/assets/images/htb-cicada/28.png)

Este usuario tiene acceso al recurso “\DEV”, vamos a acceder a dicho recurso para ver su contenido:

![](/assets/images/htb-cicada/29.png)

Podemos ver que hay un archivo en extensión “PS1”, este archivo posiblemente es un script de powershell con alguna tarea automatizada para hacer dentro del servidor de Windows, para ver su contenido, nos lo descargamos:

![](/assets/images/htb-cicada/30.png)

Este es su contenido:

![](/assets/images/htb-cicada/31.png)

Podemos ver un nombre de usuario “emily.oscars” junto con una contraseña en texto plano, ya tenemos otro nombre de usuario para volver a listar los recursos del servidor, pero al igual que antes, comprobamos que la contraseña es de verdad:

![](/assets/images/htb-cicada/32.png)

La contraseña es de verdad, así que podemo seguir.

Creo que con este usuario podremos acceder directamente a la máquina víctima, para intentarlo, usamos este comando:

![](/assets/images/htb-cicada/33.png)

![](/assets/images/htb-cicada/34.png)

Este usuario definitivamente es el mejor de todos, porque nos permitirá acceder a la máquina víctima y seguramente poder escalar a usuario administrador del sistema.

Ahora accedemos al sistema con las credenciales de este usuario:

![](/assets/images/htb-cicada/35.png)

Ya estamos dentro:

![](/assets/images/htb-cicada/36.png)

Si nos dirigimos al directorio 'Desktop', veremos la flag del usuario no privilegiado:

![](/assets/images/htb-cicada/37.png)

![](/assets/images/htb-cicada/38.png)

Y por algún motivo este usuario puede acceder al directorio de administrador del sistema, pero no puede leer el contenido del archivo 'root.txt:

![](/assets/images/htb-cicada/39.png)

![](/assets/images/htb-cicada/40.png)

Si listamos información de este usuario, veremos que pertenece al grupo de operadores de backup del sistema, seguramente por este motivo podemos acceder a ciertos directorios de la máquina:

![](/assets/images/htb-cicada/41.png)

![](/assets/images/htb-cicada/42.png)

Si vemos los privilegios que tiene este usuario, veremos que puede hacer backups de archivos y directorios:

![](/assets/images/htb-cicada/43.png)

Este privilegio se llama **SeBackupPrivilege**, vamos a buscar en Internet como podemos abusar de esto para escalar al usuario administrador:

![](/assets/images/htb-cicada/44.png)

Encontramos este recurso en GitHub que nos puede ser útil:

![](/assets/images/htb-cicada/45.png)

Según el recurso, tenemos que crear un directorio llamado **TEMP**:

![](/assets/images/htb-cicada/46.png)

Y una vez dentro, ejecutamos el siguiente comando:

![](/assets/images/htb-cicada/47.png)

Ahora realizamos una copia del archivo “sam” y lo guardamos dentro del directorio que hemos creado.

El **SAM (Security Accounts Manager)** es una base de datos crítica en sistemas Windows que almacena información de usuarios locales, incluyendo sus nombres y contraseñas (en formato hash).

Pero para poder sacar la contraseña del hash, tenemos que tener una llave maestra, y ésta se ubica en "system", y es ahí donde ejecutamos el siguiente comando:

![](/assets/images/htb-cicada/48.png)

Cuando ejecutemos los 2 comandos anteriores, validamos que los archivos estén copiamos en el directorio creado anteriormente:

![](/assets/images/htb-cicada/49.png)

Y ahora nos descargamos los 2 archivos a nuestra máquina atacante:

![](/assets/images/htb-cicada/50.png)

![](/assets/images/htb-cicada/51.png)

Con estos archivos ya podemos sacar tanto el nombre de usuario del administrador del sistema, y la contraseña en formato hash:

![](/assets/images/htb-cicada/52.png)

Ahora sí que sí, nos vamos pa' dentro:

![](/assets/images/htb-cicada/53.png)

Ya estamos dentro:

![](/assets/images/htb-cicada/54.png)

Esta es la flag del usuario administrador:

![](/assets/images/htb-cicada/55.png)


## ⚡ MACHINE PWNED ⚡

![](/assets/images/htb-cicada/56.png)
