---
title: VMware Horizon/AppVolumes LB with HAProxy and Keepalived on PhotonOS
date: '2021-08-18 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- esxi
- vsphere
- vexpert
---

En el post de hoy veremos cómo podemos balancear y dotar de alta disponibilidad a nuestros servidores de conexión de VMware Horizon y a nuestros AppVolumes Managers.

Para que mentalmente os podais hacer una idea de lo que vamos ha hacer, os dejo con el siguiente esquema

![Horizon8-architecture-design]({{ site.imagesposts2021 }}/08/Horizon8-architecture-design.png){: .align-center}

En él, podeis ver cómo añadiremos 2 nuevos servidores a nuestra infraestructura e instalaremos HAProxy + Keepalive en ellos.

# Despiegue Photon OS

![haproxy-00]({{ site.imagesposts2021 }}/08/haproxy-00.png){: .align-center}
![haproxy-01]({{ site.imagesposts2021 }}/08/haproxy-01.png){: .align-center}
![haproxy-02]({{ site.imagesposts2021 }}/08/haproxy-02.png){: .align-center}
![haproxy-03]({{ site.imagesposts2021 }}/08/haproxy-03.png){: .align-center}
![haproxy-04]({{ site.imagesposts2021 }}/08/haproxy-04.png){: .align-center}
![haproxy-05]({{ site.imagesposts2021 }}/08/haproxy-05.png){: .align-center}
![haproxy-06]({{ site.imagesposts2021 }}/08/haproxy-06.png){: .align-center}
![haproxy-07]({{ site.imagesposts2021 }}/08/haproxy-07.png){: .align-center}
![haproxy-08]({{ site.imagesposts2021 }}/08/haproxy-08.png){: .align-center}
![haproxy-09]({{ site.imagesposts2021 }}/08/haproxy-09.png){: .align-center}
![haproxy-10]({{ site.imagesposts2021 }}/08/haproxy-10.png){: .align-center}
![haproxy-11]({{ site.imagesposts2021 }}/08/haproxy-11.png){: .align-center}
![haproxy-12]({{ site.imagesposts2021 }}/08/haproxy-12.png){: .align-center}
![haproxy-13]({{ site.imagesposts2021 }}/08/haproxy-13.png){: .align-center}
![haproxy-14]({{ site.imagesposts2021 }}/08/haproxy-14.png){: .align-center}
![haproxy-15]({{ site.imagesposts2021 }}/08/haproxy-15.png){: .align-center}



Horizon8-architecture-design.png
