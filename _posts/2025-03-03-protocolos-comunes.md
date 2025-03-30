---
layout: single
title: Protocolos (TCP, UDP) y el Three-Way Handshake
date: 2025-03-05
classes: wide
header:
  teaser: /assets/images/slae32.png
categories:
  - Protocolos
tags:
  - TCP
  - UDP
---

## ¿Qué es el protocolo TCP?

El protocolo **TCP** (Transmission Control Protocol) es un protocolo orientado a conexión que se encuentra situado en la capa de transporte del modelo OSI. Tiene la función de garantizar que los datos lleguen de forma exitosa, totalmente completos y en orden desde un dispositivo de origen hasta otro de destino.

Este protocolo necesita conexión para transmitir los datos, además de que regula la velocidad de transmisión para que la red no se sature, y si un paquete se llega a perder o dañar, TCP lo reenvía. 

Algunos de los puertos más comunes de TCP son: 

- 21 **FTP** (File Transfer Protocol) - permite la transferencia de archivos entre sistemas.
- 22 **SSH** (Secure Shell) - protocolo de red seguro usado para conectarse y administrar sistemas de forma remota
- 23 **Telnet** - protocolo usado para la conexión remota a dispositivos.
- 80 **HTTP** (Hypertext Transfer Protocol) - protocolo usado para transferir datos en la World Wide Web.
- 443 **HTTPS** (Hypertext Transfer Protocol Secure) - es la versión seguira de HTTP, se usa con encriptación SSL para proteger las comunicaciones via web.

## ¿Qué es el protocolo UDP?

El protocolo **UDP** (User Datagram Protocol) es un protocolo más simple y rápido que TCP, pero cuenta con algunas desventajas: 

**· No confiable:** UDP no garantiza la entrega correcta de paquetes
**· Más inestable:** UDP no usa control de flujo, ni retransmisión de paquetes, por lo tanto es más rápido que TCP. 

Algunos de los puertos más comunes de UDP son: 

- 53 **DNS** (Domain Name System) - un sistema que traduce nombres de dominio a direcciones IP
- 123 **NTP** (Network Time Protocol) - protocolo usado para sincronizar los relojes de los dispositivos de una red
- 161 **SNMP** (Simple Network Management Protocol) - protocolo usado para administrar y supervisar los dispositivos de una red.

## ¿Qué es el famoso Three-Way Handshake?

Es una parte fundamental del protocolo **TCP**, se trata de un procedimiento usado para establecer una conexión entre 2 dispositivos. El TWH es un paso básico para crear una conexión confiable y segura para la tranferencia de paquetes en TCP. 

