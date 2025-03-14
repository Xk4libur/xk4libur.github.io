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
- [Instalar y configurar bspwm y sxhkd](#instalar-y-configurar-bspwm-y-sxhkd)
- [Instalar polybar, rofi y picom](#instalar-polybar-rofi-y-picom)
- [Instalar la terminal de kitty y configurar las fuentes](#instalar-la-terminal-de-kitty-y-configurar-las-fuentes)
- [Configurar polybar](#configurar-polybar)
- [Configurar bordes, sombras con Picom](#configurar-bordes-sombras-con-picom)


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

```bash
sudo apt install build-essential git vim libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev
```

Nos dirigimos a la carpeta de descargas del equipo y descargar los proyectos ‘bswpm‘ y ‘sxhkd‘ con los siguientes comandos:

- git clone https://github.com/baskerville/bspwm.git
- git clone https://github.com/baskerville/sxhkd.git

Para instalar cada uno de estos, hay que meternos en ambos directorios por separado y ejecutar los comandos **make** y **sudo make install** en ambos directorios.

Vamos a instalar una dependencia más de bspwm, ya que nos será de utilidad más adelante:

```bash
sudo apt install bspwm
```
Para poder configurar tanto **bspwm** como **sxhkd**, hay que editar sus archivos de configuración, estos arhivos se guardan en esta ruta:

![](/assets/images/kali-linux-install/24.png)

Pero antes de modificar nada, crearemos unos directorios de configuración para copiar esos archivos:

![](/assets/images/kali-linux-install/25.png)

Y ahora copiamos los archivos de configuración, cada uno en su directorio correspondiente:

![](/assets/images/kali-linux-install/26.png)

Ahora si que podemos empezar a editar los atajos de teclado, en el archivo **sxhkdrc**:

```bash
sudo nano ~/.config/sxhkd/sxhkdrc
```
· Lo primero que cambiaremos será el emulador de terminal que viene por defecto:

![](/assets/images/kali-linux-install/27.png)

· Cambiamos el **urxvt**, por la terminal de **kitty**:

![](/assets/images/kali-linux-install/28.png)

· Lo siguiente que cambiaremos será el lanzador de programas viene por defecto:

![](/assets/images/kali-linux-install/29.png)

· Cambiamos el que viene por defecto, por el lanzador de **rofi**:

![](/assets/images/kali-linux-install/30.png)

· Lo siguiente será cambiar esta combinación de teclas, que nos permite poder elegir una ventana de un programa en caso de tengamos más de 2 ventanas abiertas en el mismo espacio de trabajo:

![](/assets/images/kali-linux-install/31.png)

· Lo cambiaremos de la siguiente forma:

![](/assets/images/kali-linux-install/32.png)

· Lo siguiente será cambiar los preselectores, que nos permiten elegir un tamaño prefijado para una ventana antes de abrir dicha ventana, es decir, nos permitirá ver el tamaño que ocupará una aplicación antes de abrir dicha aplicación:

![](/assets/images/kali-linux-install/33.png)

· Lo cambiaremos de la siguiente forma:

![](/assets/images/kali-linux-install/34.png)

· También comentaremos todas estas combinaciones de teclado, ya que no las necesitaremos:

![](/assets/images/kali-linux-install/35.png)

· Podemos añadir editar este módulo que nos permite mover una ventana flotante dentro del entorno de bspwm, así como otro módulo que nos permita modificar el tamaño de las ventanas que ya estén abiertas:

![](/assets/images/kali-linux-install/36.png)

· Lo siguiente que haremos será crear el archivo de **bspwm_resize** para que el módulo funcione: 

![](/assets/images/kali-linux-install/37.png)

![](/assets/images/kali-linux-install/38.png)

![](/assets/images/kali-linux-install/39.png)

## Instalar polybar, rofi y picom

Para poder instalar la **polybar**, antes hay que instalar ciertas dependencias:

```bash
sudo apt install cmake cmake-data pkg-config python3-sphinx libcairo2-dev libxcb1-dev libxcb-util0-dev libxcb-randr0-dev libxcb-composite0-dev python3-xcbgen xcb-proto libxcb-image0-dev libxcb-ewmh-dev libxcb-icccm4-dev libxcb-xkb-dev libxcb-xrm-dev libxcb-cursor-dev libasound2-dev libpulse-dev libjsoncpp-dev libmpdclient-dev libcurl4-openssl-dev libnl-genl-3-dev
```
Luego, nos dirigimos al directorio 'Descargas' y ejecutamos los siguientes comandos:

```bash
git clone --recursive https://github.com/polybar/polybar
cd polybar/
mkdir build
cd build/
cmake ..
make -j$(nproc)
sudo make install
```
Para poder instalar el **picom**, instalamos los siguientes paquetes:

```bash
sudo apt install meson libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev libxcb-glx0-dev libpcre3-dev
```
Posteriormente, ejecutamos estos comandos en el directorio 'Descargas':

```bash
git clone https://github.com/ibhagwan/picom.git
cd picom/
git submodule update --init --recursive
meson --buildtype=release . build
ninja -C build
sudo ninja -C build install
```
Para poder instalar el **rofi**, solo hay que ejecutar este comando:

```bash
sudo apt install rofi
```
## Instalar la terminal de kitty y configurar las fuentes

Lo que haremos ahora será instalar el emulador de terminal que usaremos en el entorno nuevo, esta terminal se llama **Kitty** y se instala con el siguiente comando:

```bash
sudo apt install kitty
```
Una vez instalada, crearemos un directorio de configuración para la kitty en el que guardaremos 2 archivos de configuración de la terminal:

```bash
mkdir ~/.config/kitty
```
Los archivos de configuración son los siguientes:

- [kitty.conf](https://hack4u.io/wp-content/uploads/2022/09/kitty.conf_.txt)

- [color.ini](https://hack4u.io/wp-content/uploads/2022/09/color.ini_.txt)

Lo siguiente será instalar las **Hack Nerd Fonts** que es el tipo de fuentes que usaremos en la terminal.

## Configurar polybar

Para configurar la **polybar**, ejecutamos los siguientes comandos en el directorio 'Descargas': 

```bash
git clone https://github.com/VaughnValle/blue-sky.git
mkdir ~/.config/polybar
cd ~/Descargas/blue-sky/polybar/
cp * -r ~/.config/polybar
echo '~/.config/polybar/launch.sh $' >> ~/.config/bspwm/bspwmrc 
cd fonts
sudo cp * /usr/share/fonts/truetype/
fc-cache -v
```
Cuando hayamos ejecutado los comandos anteriores, deberias poder ver la polybar por la parte superior de la pantalla en el entorno de bspwm.

## Configurar bordes, sombras con Picom

Ahora toca configurar los bordes para que todo bien guapo, para ello creamos el siguiente directorio:

```bash
mkdir ~/.config/picom
```
Dentro de este directorio, añadimos el siguiente archivo de configuración: 

- [picom.conf](https://hack4u.io/wp-content/uploads/2022/09/picom.conf_.txt)