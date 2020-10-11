---
title: Configurar VMware App Volumes en HA (Alta disponibilidad)
date: '2019-07-17 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
---

Hace ya varios meses, en la serie [Creando un entorno JMP con VMware Horizon]({{ site.url }}/jmp-part1/) vimos cómo hacer la configuración e instalalación de [App Volumes]({{ site.url }}/jmp-part11/). En este post, veremos la configuración para dotar al sistema de HA y eliminar ese temido [SPOF](https://es.wikipedia.org/wiki/Single_point_of_failure)

Es lógico, que para montar nuestro App Volumes Manager en alta disponibilidad primeramente tengamos nuestra BBDD en un servidor independiente, fuera del propio App Volumes Manager. En [este post](https://miquelmariano.github.io/jmp-part11/) explicábamos la parte de nuestro servidor SQL.



# Instalación y configuración JMP Server

![jmp_db1]({{ site.imagesposts2019 }}/08/jmp_db1.png){: .align-center}
![jmp_db2]({{ site.imagesposts2019 }}/08/jmp_db2.png){: .align-center}
![jmp_db3]({{ site.imagesposts2019 }}/08/jmp_db3.png){: .align-center}
![jmp_db4]({{ site.imagesposts2019 }}/08/jmp_db4.png){: .align-center}
![jmp1]({{ site.imagesposts2019 }}/08/jmp1.png){: .align-center}
![jmp2]({{ site.imagesposts2019 }}/08/jmp2.png){: .align-center}
![jmp3]({{ site.imagesposts2019 }}/08/jmp3.png){: .align-center}
![jmp4]({{ site.imagesposts2019 }}/08/jmp4.png){: .align-center}
![jmp5]({{ site.imagesposts2019 }}/08/jmp5.png){: .align-center}
![jmp6]({{ site.imagesposts2019 }}/08/jmp6.png){: .align-center}
![jmp7]({{ site.imagesposts2019 }}/08/jmp7.png){: .align-center}
![jmp8]({{ site.imagesposts2019 }}/08/jmp8.png){: .align-center}


Espero que os sirva.

Un saludo!

Miquel.


