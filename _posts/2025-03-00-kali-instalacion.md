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

## ¿Qué es Kali Linux?

**Kali Linux** es un sistema operativo basado en Debian (una de las distribuciones de linux más famosas y estables), está orientado al sector de la ciberseguridad y el hacking ético, y es conocido como el rey de los sistemas operativos enfocados al hacking ya que está mantenido por Offensive Security. 

Para descargar la ISO de Kali, nos dirigimos a la siguiente página web:

[ISO de Kali Linux](https://www.kali.org/get-kali/#kali-installer-images)


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

Para tener un buen rendimiento en la máquina, nos dirigimos a la sección de **Pantalla**, y le subimos la memoria de video a los 128 mb, pero **sin activar la aceleración 3D**:

![](/assets/images/kali-linux-install/6.png)

Una vez hecho todo esto, ya podemos iniciar la máquina:

![](/assets/images/kali-linux-install/7.png)

