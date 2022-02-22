---
title: Modificar perfil predeterminado W10 para entornos VDI VMware Horizon
date: '2022-02-22 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- esxi
- euc
- vdi
- vexpert
---

Docu ForensiT
https://www.forensit.com/support-downloads.html

Como último paso, me gusta modificar el perfil por defecto que tiene Windows almacenado, el cual

genera ciertos iconos en el escritorio, barra de tareas, así como establecer un fondo de pantalla y los
colores del tema de Windows 10.
Para que en la creación de un nuevo perfil en nuestro escritorio virtual sea lo más estándar y no tengamos que retocarlo, lo mejor es modificar el perfil por defecto y que de esta manera todos los usuarios al iniciar por primera vez les aparezca el mismo escritorio.
Para conseguir esto de manera sencilla, existe una herramienta llamada Defprof, la cual clona un perfil de usuario que hayamos personalizado sobre el perfil por defecto de Windows.
Para poder realizar el proceso debemos arrancar nuestro Windows con un usuario cualquiera y personalizar el escritorio, los iconos, fondo de pantalla y aspecto que consideremos.
Una vez terminado, accedemos con un usuario Administrador distinto al que hemos personalizado y lanzamos el programa mediante la Línea de Comandos, indicando el perfil del usuario que hemos personalizado.



![default-profile-00]({{ site.imagesposts2022 }}/02/default-profile-00.png){: .align-center}




Hoy os traigo otro post de la serie [back to basics](https://miquelmariano.github.io/tag/#/backtobasics), que hace tiempo que no actualizaba.

Se trata de un post corto y sencillo pero que mucha gente desconoce. Se trata de ver cómo configurar un banner al hacer login en nuestros servidores ESXi por SSH.

El proceso es muy sencillo, simplemente tendremos que editar el fichero  `vi /etc/issue` con el mensaje que queramos mostrar.

Una vez editado el fichero, reiniciaremos SSH con el siguiente comando:

```ssh
/etc/init.d/SSH restart
```

En mi caso, el resultado es este:

![esxi-banner]({{ site.imagesposts2021 }}/01/esxi-banner.png){: .align-center}

¿Qué os parece?

Por cierto, si quereis hacer algún tipo de extravagancia, esta [herramienta online](http://patorjk.com/software/taag/#p=testall&f=Arrows&t=miquelmariano.github.io) que me he encontrado está muy bien

Espero que os guste ;-)

Saludos!

Miquel.


