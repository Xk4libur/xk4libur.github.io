---
layout: single
title: ¿Qué es un sistema operativo?
excerpt: "En el mundo de la informática, existe la palabra tan conocida como “sistema operativo”, todo el mundo usa o ha usado un sistema operativo en algún momento de su vida, ya sea en el pc o en un teléfono. Pero, ¿qué es realmente un sistema operativo?"
date: 2025-03-25
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Linux
tags:
  - Linux
---

El **sistema operativo es una de las 3 capas** que conforman un ordenador: 

- **Software**: (navegador, explorador de archivos, etc.)
- **Sistema operativo**: (Windows, Linux)
- **Hardware**: (componentes físicos del ordenador)

Cada una de las 3 capas realiza una función esencial dentro del ordenador, la función del sistema operativo es servir de puente o intermediario entre la capa del software y la capa del hardware, proporcionando al software los recursos que necesita para funcionar, y estos recursos los recoge de la capa del hardware.

## ¿Qué tipos de sistemas operativos hay?

No solo existen sistemas operativos como Windows, Linux o macOS, también existen sistemas operativos enfocados a sectores en particular para un uso específico.

### Sistemas operativos de uso general: 

Son los sistemas operativos más usados en el mundo doméstico, se usan en ordenadores personales, servidores, y dispositivos móviles.

Algunos ejemplos son: 

- **Windows**:

![](/assets/images/sistema-operativo/1.png)

- **Linux**:

![](/assets/images/sistema-operativo/2.png)

- **macOS**:

![](/assets/images/sistema-operativo/3.png)

- **Android**:

![](/assets/images/sistema-operativo/4.png)

- **iOS**:

![](/assets/images/sistema-operativo/5.png)


## ¿Qué es Linux?

Linux es un núcleo de código abierto a partir del cual se pueden construir sistemas operativos basados en Linux, existen muchos sistemas operativos basados en el kernel de Linux, y a dichos sistemas operativos reciben el nombre de distribuciones de Linux.

Una de las distribuciones de Linux más populares es **Ubuntu**, es un sistema operativo basado en Debian, y es de las más fáciles de instalar y usar:

![](/assets/images/sistema-operativo/6.png)

## Como instalar Virtualbox

Virtualbox es un software que permite crear máquinas virtuales para simular sistemas operativos, de tal forma que podemos usar otros sistemas operativos sin que el nuestro sea afectado.

![](/assets/images/sistema-operativo/7.png)

Para instalar Virtualbox, simplemente nos dirigimos al sitio web oficial, para eso buscamos Virtualbox en el navegador y nos dirigimos a la página web:

![](/assets/images/sistema-operativo/8.png)

![](/assets/images/sistema-operativo/10.png)

Hacemos clic en “Descargas” para descargar el archivo para instalar el programa:

![](/assets/images/sistema-operativo/11.png)

Seleccionamos para que sistema operative queremos instalar, en mi caso será para Windows, aunque también se puede hacer para Linux y macOS:

![](/assets/images/sistema-operativo/12.png)

En el caso de Windows, hacemos doble clic en el archivo de instalación, y solo hacemos clic en **Siguiente** y **Aceptar** o **Instalar**:

![](/assets/images/sistema-operativo/13.png)


## Instalación de Ubuntu en Virtualbox

Para descargar la ISO de Ubuntu, nos dirigimos a la siguiente página web:

[**- Link a la web Ubuntu**](https://ubuntu.com/download/desktop)

En mi caso aparece la versión de **Ubuntu 24.04.2 LTS**, este caso es la **“Long Time Support”** o también llamado la versión de “Soporte de Largo Termino”, esta versión es la que tiene más tiempo de actualizaciones de seguridad y mantenimiento, lo que ayuda a que la distribución se pueda usar durante mucho tiempo.

![](/assets/images/sistema-operativo/14.png)

Una vez descargada la imagen ISO de Ubuntu, hacemos clic en “Nueva” para empezar a crear una máquina desde 0:

![](/assets/images/sistema-operativo/15.png)

Le ponemos un nombre a la máquina y le añadimos la imagen ISO de Ubuntu:

![](/assets/images/sistema-operativo/16.png)

Añadimos recursos del sistema a la máquina, como la memoria RAM, la cantidad de núcleos de la CPU y la capacidad de almacenamiento del disco para la máquina:

![](/assets/images/sistema-operativo/17.png)

![](/assets/images/sistema-operativo/18.png)

Para aumentar el rendimiento de la máquina, añadimos memoria de video y activamos la aceleración 3D:

![](/assets/images/sistema-operativo/19.png)

Una vez hecho esto, iniciamos la máquina:

![](/assets/images/sistema-operativo/20.png)

Seleccionamos el idioma principal:

![](/assets/images/sistema-operativo/21.png)

Seleccionamos el idioma del teclado:

![](/assets/images/sistema-operativo/22.png)

Nos preguntará si queremos conectarnos a Internet, en nuestro caso le decimos que no será necesario:

![](/assets/images/sistema-operativo/23.png)

Ubuntu nos preguntará si queremos instalar el sistema operativo en la máquina o usarlo como una distribución en Live, es decir, sin instalarlo. En nuestro caso, lo instalaremos desde 0 ya que estamos usando una máquina virtual:

![](/assets/images/sistema-operativo/24.png)

Tambien nos preguntará si queremos instalar software adicional y actualizaciones del sistema, este paso nos ahorrará tiempo después de la instalación, entonces marcamos las 2 opciones:

![](/assets/images/sistema-operativo/25.png)

Antes de instalarlo, nos preguntará sobre las particiones que queremos hacer en el disco duro de la máquina virtual, en este caso, elegimos la primera opción ya que es la más sencilla de todas y nos evitará tener que hacer las particiones de forma manual:

![](/assets/images/sistema-operativo/26.png)

Incluimos el nombre del usuario, así como el nombre de la máquina y una contraseña para el usuario:

![](/assets/images/sistema-operativo/27.png)

Elegimos la zona horaria:

![](/assets/images/sistema-operativo/28.png)

Antes de finalizar al instalación, nos aparecerá un pequeño resumen de las modificaciones que se harán en el sistema:

![](/assets/images/sistema-operativo/29.png)

Y finalmente, la instalación de Ubuntu ha terminado:

![](/assets/images/sistema-operativo/30.png)

