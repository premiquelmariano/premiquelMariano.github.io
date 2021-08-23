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

# Configuración inicial

Una vez tengamos desplegadas las 2 VMs haremos una pequeña configuración inicial para empezar.

- Actualizamos el SO

```ssh
tdnf upgrade -y
```

- Configurar IP estática
Por defecto, el fichero de configuración de IP se encuentra en `/etc/systemd/network/99-dhcp-en.network`

Con nuestro editor de textos preferido (vim, por ejemplo), deshabilitaremos DHCP
```ssh
[Match]
Name=e*
[Network]
DHCP=no
```

Crearemos un nuevo fichero de configuración con la siguiente configuración y lo llamaremos `/etc/systemd/network/10-static-en.network`
```ssh
[Match]

Name=eth0
[Network]
Address=192.168.6.120/24
Gateway=192.168.6.1
DNS=192.168.6.100
[DHCP]
UseDNS=false
```

> **_NOTA:_** Pondremos la IP correspondiente a cada uno de los servidores

- Cambiaremos el propietario del fichero con el siguiente comando: `chown systemd-network:systemd-network /etc/systemd/network/10-static-en.network`

Para poder usar las VIP en ambos nodos de Keepalive y HAProxy, será necesario realizar ciertos cambios para permitir el reenvio a nivel IP y permitir que ambos servicios usen una IP que no está definida en la interfaz física de la VM.

Por defecto, PhotonOS tiene este comportamiento deshabilitado y lo podremos habilitar de la siguiente manera:

- Editamos el fichero de configuración `etc/sysctl.d/55-keepalived.conf`

```ssh
#Enable IPv4 Forwarding
net.ipv4.ip_forward = 1
#Enable non-local IP bind
net.ipv4.ip_nonlocal_bind = 1
```

> **_NOTA:_** Fijaros que en la misma carpeta, está un fichero llamado `50-security-hardening.conf`. Al usar nosotros un numero superior en el fichero creado, es posible que se sobreescriban algunas configuraciones definidas por defecto.


