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

En el breve post de hoy veremos cómo realizar una actualizacion de firmware en nuestros switches Brocade de nuestra SAN.

*IMPORTANTE*Hay que tener en cuenta que cualquier actualización de firmware en cualquier dispositivo en general es una operación que debe realizarse por personal cualificado. En el caso de nuestra SAN, una mala planificación en el proceso de actualización (no seguir el orden correcto, no comprobar la compatibilidad de nuestros dispositivos...) podria generar problemas graves en el acceso al almacenamiento, incluso provocar disrupción de servicio.
{: .notice}

Para ello los switch Brocade ofrecen la posibilidad de hacer backup mediante scp o ftp. Vamos a ver como implementar los backups mediante el comando `configupload`.

En este ejemplo utilizaremos un FTP como repositorio para guardar el backup:

Si no teneis ningún servidor FTP en vuestra infraestructura, os animo que visiteis [este post](https://miquelmariano.github.io/2017/07/xlight-FTP) donde explico como montar uno "portable"
{: .notice}



![firmware1]({{ site.imagesposts2019 }}/09/firmware1.png){: .align-center}
![firmware2]({{ site.imagesposts2019 }}/09/firmware2.png){: .align-center}
![firmware3]({{ site.imagesposts2019 }}/09/firmware3.png){: .align-center}
![firmware4]({{ site.imagesposts2019 }}/09/firmware4.png){: .align-center}

También disponemos del comando `firmwaredownloadstatus` que nos dará información de todo el proceso de actualización:

![firmware5]({{ site.imagesposts2019 }}/09/firmware5.png){: .align-center}


Espero que os sea de utilidad.
Gracias por compartir

Un saludo

Miquel.



