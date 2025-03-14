---
layout: single
title: Instalación y personalización de Kali Linux (SIN TERMINAR)
excerpt: "En este artículo explico como instalar kali linux en una máquina virtual y cómo personalizar este sistema operativo paso a paso para convertirlo en un entorno profesional de trabajo."
date: 2025-03-12
classes: wide
header:
 teaser_home_page: true
categories:
  - linux
tags:  
  - custom
---

# Índice
- [¿Qué es Kali Linux?](#qué-es-kali-linux)
- [Creación de la máquina virtual](#creacion-de-la-maquina-virtual)
- [Instalar Kali Linux](#instalar-kali-linux)
- [Actualizar Kali Linux](#actualizar-kali-linux)


## ¿Qué es Kali Linux?

**Kali Linux** es un sistema operativo basado en Debian (una de las distribuciones de linux más famosas y estables), está orientado al sector de la ciberseguridad y el hacking ético, y es conocido como el rey de los sistemas operativos enfocados al hacking ya que está mantenido por Offensive Security. 

Para descargar la ISO de Kali, nos dirigimos a la siguiente página web:

[ISO de Kali Linux](https://www.kali.org/get-kali/#kali-installer-images)

## Creación de la máquina virtual

Al ingresar a la web, nos aparecerán varias versiones de la ISO, elegimos la opción **recommended**:

![](/assets/images/kali-linux-install/1.png)

Cuando tengamos descargado el archivo .ISO, nos dirigimos al software que usaremos para virtualizarlo, en mi caso usaré **Virtualbox**:

Empezamos creando una nueva máquina virtual:

![](/assets/images/kali-linux-install/2.png)

Ponemos un nombre a la máquina y le asignamos la ISO de Kali Linux:

![](/assets/images/kali-linux-install/3.png)

Le asignamos los recursos del sistema, como la memoria RAM y los núcleos de la CPU que tendrá la máquina virtual:

![](/assets/images/kali-linux-install/4.png)

Añadimos el disco duro de almacenamiento que tendrá la máquina:

![](/assets/images/kali-linux-install/5.png)

Para tener un buen rendimiento en la máquina, nos dirigimos a la sección de **Pantalla**, y le subimos la memoria de video a los 128 MB, pero **sin activar la aceleración 3D**:

![](/assets/images/kali-linux-install/6.png)

Una vez hecho todo esto, ya podemos iniciar la máquina:

![](/assets/images/kali-linux-install/7.png)

## Instalar Kali Linux

Elegimos el idioma:

![](/assets/images/kali-linux-install/8.png)

Incluimos el nombre de host que tendrá Kali para identificarse en la red:

![](/assets/images/kali-linux-install/9.png)

Elegimos un nombre de usuario y una contraseña:

![](/assets/images/kali-linux-install/10.png)

![](/assets/images/kali-linux-install/11.png)

Elegimos el tipo de particionado del disco, así como el disco de la máquina virtual:

![](/assets/images/kali-linux-install/12.png)

![](/assets/images/kali-linux-install/13.png)

![](/assets/images/kali-linux-install/14.png)

Aplicamos los cambios:

![](/assets/images/kali-linux-install/15.png)

![](/assets/images/kali-linux-install/16.png)

Seleccionamos los programas así como el entorno de escritorio que se instalarán por defecto:

![](/assets/images/kali-linux-install/17.png)

Y por último, instalamos el GRUB para el arranque de Kali Linux al iniciar la máquina:

![](/assets/images/kali-linux-install/18.png)

![](/assets/images/kali-linux-install/19.png)

## Actualizar Kali Linux

En sistemas operativos Linux se ha de actualizar por terminal usando comandos de bash, para este caso, abrimos la terminal y ejecutamos los siguiente comandos:

· Para ver cuantos paquetes se pueden actualizar, ejecutamos este comando:

![](/assets/images/kali-linux-install/20.png)

· Podemos ver la cantidad de paquetes que se pueden actualizar:

![](/assets/images/kali-linux-install/21.png)

· Para actualizarlos, ejecutamos el siguiente comando y confirmamos:

![](/assets/images/kali-linux-install/22.png)

![](/assets/images/kali-linux-install/23.png)

## Instalar y configurar bspwm y sxhkd

Antes de nada, vamos a instalar algunas dependencias necesarias:

```apt install build-essential git vim libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev```


