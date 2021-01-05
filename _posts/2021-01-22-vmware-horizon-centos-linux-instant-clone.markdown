---
title: Configurar VMware Horizon desktop pool con CentOS 8
date: '2021-01-22 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
- centos8
---

https://tech.iot-it.no/vmware-horizon-centos-linux-8-instant-clone-desktop-pool/

https://computingforgeeks.com/join-centos-rhel-system-to-active-directory-domain/

Estos últimos días me ha dado por trastear con CentOS 8 y queria ver si era capaz de montar un pool de Instant Clones con Horizon 8. No ha sido tarea fácil, pero creo que lo he conseguido. Ahí va el proceso que he seguido:

# Desplegar nueva VM plantilla

Cómo siempre que trabajamos con VDI, necesitaremos una plantilla base, a partir de la cual, se desplegaran los escritorios. La plantilla que he creado para CentOS 8 tiene los siguientes parámetros:

![instalar-so-00]({{ site.imagesposts2021 }}/01/instalar-so-00.png){: .align-center}
![instalar-so-01]({{ site.imagesposts2021 }}/01/instalar-so-01.png){: .align-center}
![instalar-so-02]({{ site.imagesposts2021 }}/01/instalar-so-02.png){: .align-center}
![instalar-so-03]({{ site.imagesposts2021 }}/01/instalar-so-03.png){: .align-center}
![instalar-so-04]({{ site.imagesposts2021 }}/01/instalar-so-04.png){: .align-center}
![instalar-so-05]({{ site.imagesposts2021 }}/01/instalar-so-05.png){: .align-center}
![instalar-so-06]({{ site.imagesposts2021 }}/01/instalar-so-06.png){: .align-center}
![instalar-so-07]({{ site.imagesposts2021 }}/01/instalar-so-07.png){: .align-center}
![instalar-so-08]({{ site.imagesposts2021 }}/01/instalar-so-08.png){: .align-center}
![instalar-so-09]({{ site.imagesposts2021 }}/01/instalar-so-09.png){: .align-center}
![instalar-so-10]({{ site.imagesposts2021 }}/01/instalar-so-10.png){: .align-center}

En la KB ["Changed Block Tracking (CBT) on virtual machines (1020128)](https://kb.vmware.com/s/article/1020128) especifica lo siguiente:

“If you are using VMware Horizon View and linked clone or instant clone virtual machines, you should not be using CBT. Always ensure that CBT is disabled for the parent virtual machine.”
{: .alert .alert-warning}

Para ello, añadiremos estos dos parámetros en la configuración avanzada de la VM

```
ctkEnabled = FALSE
scsi0:0.ctkEnabled = FALSE
```

![instalar-so-11]({{ site.imagesposts2021 }}/01/instalar-so-11.png){: .align-center}
![instalar-so-12]({{ site.imagesposts2021 }}/01/instalar-so-12.png){: .align-center}
![instalar-so-13]({{ site.imagesposts2021 }}/01/instalar-so-13.png){: .align-center}
![instalar-so-14]({{ site.imagesposts2021 }}/01/instalar-so-14.png){: .align-center}

# Instalar sistema operativo

![instalar-so-15]({{ site.imagesposts2021 }}/01/instalar-so-15.png){: .align-center}
![instalar-so-16]({{ site.imagesposts2021 }}/01/instalar-so-16.png){: .align-center}
![instalar-so-17]({{ site.imagesposts2021 }}/01/instalar-so-17.png){: .align-center}
![instalar-so-18]({{ site.imagesposts2021 }}/01/instalar-so-18.png){: .align-center}
![instalar-so-19]({{ site.imagesposts2021 }}/01/instalar-so-19.png){: .align-center}
![instalar-so-20]({{ site.imagesposts2021 }}/01/instalar-so-20.png){: .align-center}
![instalar-so-21]({{ site.imagesposts2021 }}/01/instalar-so-21.png){: .align-center}
![instalar-so-22]({{ site.imagesposts2021 }}/01/instalar-so-22.png){: .align-center}
![instalar-so-23]({{ site.imagesposts2021 }}/01/instalar-so-23.png){: .align-center}
![instalar-so-24]({{ site.imagesposts2021 }}/01/instalar-so-24.png){: .align-center}
![instalar-so-25]({{ site.imagesposts2021 }}/01/instalar-so-25.png){: .align-center}
![instalar-so-26]({{ site.imagesposts2021 }}/01/instalar-so-26.png){: .align-center}
![instalar-so-27]({{ site.imagesposts2021 }}/01/instalar-so-27.png){: .align-center}
![instalar-so-28]({{ site.imagesposts2021 }}/01/instalar-so-28.png){: .align-center}
![instalar-so-29]({{ site.imagesposts2021 }}/01/instalar-so-29.png){: .align-center}
![instalar-so-30]({{ site.imagesposts2021 }}/01/instalar-so-30.png){: .align-center}
![instalar-so-31]({{ site.imagesposts2021 }}/01/instalar-so-31.png){: .align-center}
![instalar-so-32]({{ site.imagesposts2021 }}/01/instalar-so-32.png){: .align-center}
![instalar-so-33]({{ site.imagesposts2021 }}/01/instalar-so-33.png){: .align-center}
![instalar-so-34]({{ site.imagesposts2021 }}/01/instalar-so-34.png){: .align-center}
![instalar-so-35]({{ site.imagesposts2021 }}/01/instalar-so-35.png){: .align-center}
![instalar-so-36]({{ site.imagesposts2021 }}/01/instalar-so-36.png){: .align-center}

# Instalar agentes

## VMware Tools

![agentes-00]({{ site.imagesposts2021 }}/01/agentes-00.png){: .align-center}
![agentes-01]({{ site.imagesposts2021 }}/01/agentes-01.png){: .align-center}
![agentes-02]({{ site.imagesposts2021 }}/01/agentes-02.png){: .align-center}
![agentes-03]({{ site.imagesposts2021 }}/01/agentes-03.png){: .align-center}
![agentes-04]({{ site.imagesposts2021 }}/01/agentes-04.png){: .align-center}
![agentes-05]({{ site.imagesposts2021 }}/01/agentes-05.png){: .align-center}
![agentes-06]({{ site.imagesposts2021 }}/01/agentes-06.png){: .align-center}
![agentes-07]({{ site.imagesposts2021 }}/01/agentes-07.png){: .align-center}
![agentes-08]({{ site.imagesposts2021 }}/01/agentes-08.png){: .align-center}

## Horizon Agent

![horizon-agent-00]({{ site.imagesposts2021 }}/01/horizon-agent-00.png){: .align-center}

# Meter plantilla en dominio

# Desplegar nuevo deskop pool de Instant Clone

# Principal handicap

Gestión de perfiles y datos de usuario
Soporte 1:1 con FD para no necesitar gestión de perfiles

https://communities.vmware.com/t5/Dynamic-Environment-Manager/UEM-and-Horizon-Linux-Desktop/m-p/1386499


![instalar-so-00]({{ site.imagesposts2021 }}/01/instalar-so-00.png){: .align-center}

¿Qué os parece?

Por cierto, si quereis hacer algún tipo de extravagancia, esta [herramienta online](http://patorjk.com/software/taag/#p=testall&f=Arrows&t=miquelmariano.github.io) que me he encontrado está muy bien

Espero que os guste ;-)

Saludos!

Miquel.


