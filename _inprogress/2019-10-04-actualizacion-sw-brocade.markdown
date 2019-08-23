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

En el breve post de hoy, veremos como de una forma sencilla podemos realizar un backup de la configuración de los switchs de nuestra SAN.

Para ello los switch Brocade ofrecen la posibilidad de hacer backup mediante scp o ftp. Vamos a ver como implementar los backups mediante el comando `configupload`.

En este ejemplo utilizaremos un FTP como repositorio para guardar el backup:

Si no teneis ningún servidor FTP en vuestra infraestructura, os animo que visiteis [este post](https://miquelmariano.github.io/2017/07/xlight-FTP) donde explico como montar uno "portable"
{: .notice}



![firmware1]({{ site.imagesposts2019 }}/09/firmware1.png){: .align-center}
![firmware2]({{ site.imagesposts2019 }}/09/firmware2.png){: .align-center}
![firmware3]({{ site.imagesposts2019 }}/09/firmware3.png){: .align-center}


Espero que os sea de utilidad.
Gracias por compartir

Un saludo

Miquel.



