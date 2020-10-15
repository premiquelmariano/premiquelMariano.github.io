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

![appvolumes-diagram]({{ site.imagesposts2020 }}/10/appvolumes-diagram.png){: .align-center} 

# Instalación segundo App Volumes Manager

![appvolumes-install-01]({{ site.imagesposts2020 }}/10/appvolumes-install-01.png){: .align-center} 
![appvolumes-install-02]({{ site.imagesposts2020 }}/10/appvolumes-install-02.png){: .align-center} 
![appvolumes-install-03]({{ site.imagesposts2020 }}/10/appvolumes-install-03.png){: .align-center} 
![appvolumes-install-04]({{ site.imagesposts2020 }}/10/appvolumes-install-04.png){: .align-center} 
![appvolumes-install-05]({{ site.imagesposts2020 }}/10/appvolumes-install-05.png){: .align-center} 
![appvolumes-install-06]({{ site.imagesposts2020 }}/10/appvolumes-install-06.png){: .align-center} 
![appvolumes-install-07]({{ site.imagesposts2020 }}/10/appvolumes-install-07.png){: .align-center} 
![appvolumes-install-08]({{ site.imagesposts2020 }}/10/appvolumes-install-08.png){: .align-center} 
![appvolumes-install-09]({{ site.imagesposts2020 }}/10/appvolumes-install-09.png){: .align-center} 
![appvolumes-install-10]({{ site.imagesposts2020 }}/10/appvolumes-install-10.png){: .align-center} 
![appvolumes-install-11]({{ site.imagesposts2020 }}/10/appvolumes-install-11.png){: .align-center} 
![appvolumes-install-12]({{ site.imagesposts2020 }}/10/appvolumes-install-12.png){: .align-center} 

# Configurar NLB

![appvolumes-install-13]({{ site.imagesposts2020 }}/10/appvolumes-install-13.png){: .align-center} 

# Reconfigurar App Volumes Agent

![appvolumes-install-14]({{ site.imagesposts2020 }}/10/appvolumes-install-14.png){: .align-center} 

HKLM\System\CurrentControlSet\services\svservice\parameters 

https://www.simonlong.co.uk/blog/2015/04/11/appvolumes-add-multiple-app-volume-manager-addresses-to-the-app-volumes-agent/


Espero que os sirva.

Un saludo!

Miquel.


