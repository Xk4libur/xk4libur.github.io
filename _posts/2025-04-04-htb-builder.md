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

Al parecer no podemos ejecutar código bash en la consola de la web:

![](/assets/images/htb-builder/40.png)

Hay una forma de poder ejecutar comandos en la terminal de la web, primero buscamos esto en el navegador:

![](/assets/images/htb-builder/41.png)

Nos encontramos con este script:

![](/assets/images/htb-builder/42.png)

Nos copiamos el script entero en la máquina atacante, pero para usarlo tenemos que modificar esta parte:

![](/assets/images/htb-builder/43.png)

La idea de esto es modificar el código de este comando para que sea una reverse shell codificado en Base64. 

Podemos ver que si decodificamos el código actual, veremos esto:

![](/assets/images/htb-builder/44.png)

Lo que haremos será codificar una reverse shell para nuestro caso actual codificada en Base64:

![](/assets/images/htb-builder/45.png)

Copiamos el comando codificado en Base64 en el script que nos copiamos anteriormente en nuestra máquina atacante:

![](/assets/images/htb-builder/46.png)

Nos ponemos en escucha por el puerto que habiamos puesto en el código:

![](/assets/images/htb-builder/47.png)

Lanzamos y ejecutamos el script en la web:

![](/assets/images/htb-builder/48.png)

Y nos vamos pa' dentro:

![](/assets/images/htb-builder/49.png)

Antes de ejecutar ningún comando, realizamos un tratamiento de la tty para que la terminal no explote:

![](/assets/images/htb-builder/50.png)

![](/assets/images/htb-builder/51.png)

![](/assets/images/htb-builder/52.png)

Podemos ver que en el directorio **/home**, no hay nada de nada:

![](/assets/images/htb-builder/53.png)

Pero si nos dirigimos a esta ruta, veremos la flag del usuario no privilegiado:

![](/assets/images/htb-builder/54.png)

![](/assets/images/htb-builder/55.png)

En la máquina no se puede hacer nada más para tratar de conseguir los datos del usuario privilegiado, volvamos a la web para investigar.

Encontramos esta opción dentro de la web:

![](/assets/images/htb-builder/56.png)

Dentro hay una opción de **Credentials**:

![](/assets/images/htb-builder/57.png)

Dentro se encuentra el usuario root del sistema, si intentamos actualizar sus credenciales, veremos esto:

![](/assets/images/htb-builder/58.png)

Al parecer se encuentra la clave privada SSH del usuario privilegiado, pero por algún motivo no podemos verla **a simple vista**:

![](/assets/images/htb-builder/59.png)

Que no se pueda ver en la web, no significa que no se pueda ver en el código de la misma. 

Vamos a poner el cursor del ratón sobre el icono de la clave y seleccionamos **Inspeccionar**:

![](/assets/images/htb-builder/60.png)

![](/assets/images/htb-builder/61.png)

Al final si que conseguimos obtener la clave privada dentro del código:

![](/assets/images/htb-builder/62.png)

Lo que haremos será copiarnos la clave en nuestra máquin atacante:

![](/assets/images/htb-builder/63.png)

Lo que tenemos que hacer ahora es tratar de inyectar la clave codificada en la web para que nos devuelva la clave SSH en texto plano, como hicimos anteriormente para ejecutar la reverse shell.

Para eso nos dirigimos a este repositorio:

![](/assets/images/htb-builder/65.png)

![](/assets/images/htb-builder/66.png)

Reemplazamos la clave que viene por defecto por la que tenemos en nuestra máquina atacante:

![](/assets/images/htb-builder/68.png)

Y ya tenemos la clave privada SSH del usuario privilegiado:

![](/assets/images/htb-builder/69.png)

Para ingresar a la máquina como usuario privilegiado, simplemente nos copiamos la clave en nuestra máquina atacante:

![](/assets/images/htb-builder/70.png)

Le damos los siguiente permisos a dicha clave:

![](/assets/images/htb-builder/71.png)

Y nos vamos pa' dentro de la máquina como **root**:

![](/assets/images/htb-builder/72.png)

![](/assets/images/htb-builder/73.png)

Nada más entremos en la máquina, tendremos la flag del usuario privilegiado:

![](/assets/images/htb-builder/74.png)


## ⚡ MACHINE PWNED ⚡