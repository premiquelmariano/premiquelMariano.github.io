---
title: Back-to-basics 7 - Contadores importantes de CPU
date: '2018-02-28 00:00:00'
layout: post
image: /assets/images/posts/2019/02/performance.jpg
headerImage: true
tag:
- vmware
- vsphere
- vexpert
- devops
- backtobasics
category: blog
author: miquelMariano
description: En este post vamos a ver los contadores mas importantes de CPU que nos podemos encontrar en cada VM de nuestro entorno.
hidden: false
comments: true
permalink: /basics7counters/
---

http://www.yellow-bricks.com/2012/07/17/why-is-wait-so-high/

Buenos dias a tod@as!!

En esta séptima entrada de la serie [back-to-basics](https://miquelmariano.github.io/tags/#backtobasics), me gustaria hablar un poco de los conadores de CPU mas importantes quen podemos encontrar en una máquina virtual.

Todo esto viene a raíz de un debate que tuvimos hace unas semanas el bueno de [Pablo](https://twitter.com/eclat2k) y yo.


![esxtop1]({{ site.imagesposts2019 }}/02/esxtop1.png)

RUN - Tiempo que una VM está confumiendo recursos de CPU
WAIT - Tiempo que una VM está esperando al VMkernel
READY - Tiempo que la VM está esperando recursos de CPU
CO-STOP - Tiempo que la VM está esperando que se alineen las CPU para asignarselas (solo en VM con mas de 1 CPU)


Un saludo!

Miquel.


