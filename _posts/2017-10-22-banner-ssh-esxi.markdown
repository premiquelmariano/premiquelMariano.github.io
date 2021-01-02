---
title: Back-to-basics 11 - Configurar SSH Login banner en ESXi
date: '2021-01-22 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- esxi
- vsphere
- vexpert
---

Hoy os traigo otro post de la serie [back to basics](https://miquelmariano.github.io/tag/#/backtobasics), que hace tiempo que no actualizaba.

Se trata de un post corto y sencillo pero que mucha gente desconoce. Se trata de ver cómo configurar un banner al hacer login en nuestros servidores ESXi por SSH.

El proceso es muy sencillo, simplemente tendremos que editar el fichero  `vi /etc/issue` con el mensaje que reramos mostrar.

Una vez editado el fichero, reiniciaremos SSH con el siguiente comando:

```ssh
/etc/init.d/SSH restart
```

En mi caso, el resultado es este:

![esxi-banner]({{ site.imagesposts2021 }}/01/esxi-banner.png){: .align-center}

¿Qué os parece?

Por cierto, si quereis hacer algún tipo de extravagancia, esta [herramienta online](http://patorjk.com/software/taag/#p=testall&f=Arrows&t=miquelmariano.github.io) que me he encontrado está muy bién

Espero que os guste ;-)

Saludos!

Miquel.


