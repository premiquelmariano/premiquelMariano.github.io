---
title: Actualización de firmware en switches Brocade FC
date: '2017-10-04 00:00:00'
layout: post
image: /assets/images/posts/2017/10/brocade-logo.png
tag:
- firmware
- brocade
- fabric
- san
- fc
---

Buenos días a tod@s!!!

En el post de hoy veremos cómo realizar una actualización de firmware en nuestros switches Brocade de nuestra SAN.

**IMPORTANTE** Hay que tener en cuenta que cualquier actualización de firmware en cualquier dispositivo en general es una operación que debe realizarse por personal cualificado. En el caso de nuestra SAN, una mala planificación en el proceso de actualización (no seguir el orden correcto, no comprobar la compatibilidad de nuestros dispositivos...) podría generar problemas graves en el acceso al almacenamiento, incluso provocar disrupción de servicio.
{: .notice}

Como comentaba anteriormente, la actualización de firmware debe realizarse por personal cualificado, y en cualquier caso, [hacer un backup de la configuración antes de comenzar](https://miquelmariano.github.io/2017/10/backup-configuracion-sw-brocade)

# Preparar repositorio FTP con el firmware

La mejor opción para cargar el firmware en los switches es hacerlo por FTP, de esta manera nos evitamos el desplazamiento para tener que poner un USB (que es otra forma de cargar el firmware)

Hace tiempo, [publiqué un post para montar un pequeño FTP portable](https://miquelmariano.github.io/2017/07/xlight-FTP). Es el momento de ponerlo en práctica :-)

![PoD1]({{ site.imagesposts2019 }}/10/PoD1.jpg){: .align-center}
![PoD2]({{ site.imagesposts2019 }}/10/PoD2.jpg){: .align-center}
![PoD3]({{ site.imagesposts2019 }}/10/PoD3.png){: .align-center}
![PoD4]({{ site.imagesposts2019 }}/10/PoD4.png){: .align-center}
![PoD5]({{ site.imagesposts2019 }}/10/PoD5.png){: .align-center}
![PoD6]({{ site.imagesposts2019 }}/10/PoD6.png){: .align-center}
![PoD7]({{ site.imagesposts2019 }}/10/PoD7.png){: .align-center}
![PoD8]({{ site.imagesposts2019 }}/10/PoD8.png){: .align-center}

Espero que os sea de utilidad.
Gracias por compartir

Un saludo

Miquel.



