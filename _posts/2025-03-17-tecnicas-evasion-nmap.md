---
layout: single
title: Tecnicas de evasión de Firewalls con Nmap
excerpt: "Nmap y los Firewalls nunca se han llevado bien entre ellos, mientras que uno trata de buscar vulnerabilidades o hosts en la red, otro trata de controlar y vigilar el tráfico de red para que no haya nada fuera de lo común."
date: 2025-03-17
classes: wide
header:
 teaser_home_page: true
categories:
  - nmap
tags:
  - reconocimiento  
---

Al momento de hacer pruebas de pentesting, uno de los desafíos más grandes es evitar la detección de los **Firewalls**.

Un **Firewall** es un sistema diseñado para proteger las redes informáticas de posibles amenazas, para evitar este sistema, Nmap posee una variedad de técnicas de evasión que permiten a los atacantes hacer escaneos sigilosos y de esta forma evitar la detección de los Firewalls.

## Ejemplos de parámetros con Nmap para evadir Firewalls:

- **MTU (--mtu)**: este parámetro conocido como “Maximum Transmission Unit” permite ajustar el tamaño de los paquetes que se envían para evitar la detección de los Firewalls. Nmap puede configurar manualmente el tamaño máximo de los paquetes para que así sean los suficientemente pequeños para pasar por el Firewall sin ser detectados.

```bash
nmap -p22 --mtu 8 <IP>
```
En este ejemplo se envían paquetes con un tamaño **máximo de 8 bytes**, al ser los paquetes muy pequeños, éstos pasan desapercibidos por el firewall.

Algunos firewalls puede bloquear paquetes a partir un tamaño estándar, pero no son capaces de detectar fragmentos pequeños de dichos paquetes.

**Source Port (--source-port)**: este parámetro permite "simular" un envío de paquetes a través de un puerto específico, ya que puede ser que los firewalls estén configurados para recibir paquetes a través de ciertos puertos de confianza.

```bash
nmap --source-port 53 <IP>
```

En este ejemplo se envían paquetes a través del **puerto 53** de la máquina atacante, de esta forma los paquetes serán recibidos por la víctima a través de este puerto.

En este ejemplo, se falsifica el puerto de origen de los paquetes como si provinieran del puerto 53, pero en realidad la máquina atacante está usando otro puerto para enviarlos.

Algunos firewalls pueden confiar en este tráfico y dejarlo pasar, creyendo que proviene de un servidor DNS legítimo, lo que podría ayudar a evadir ciertas restricciones de seguridad.