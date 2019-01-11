---
title: Ansible AWX - Part 1 - Instalación
date: '2017-09-22 00:00:00'
layout: post
image: /assets/images/posts/2018/08/awx-logo.png
headerImage: true
tag:
- automation
- ansible
- devops
category: blog
author: miquelMariano
description: Ansible AWX - Part 1 - Instalación
hidden: false
comments: true
permalink: /awx/
---

Buenos dias a tod@as!!

Hace unos meses, el gran Jorge de la Cruz, [publicó en su blog un post](https://www.jorgedelacruz.es/2018/08/15/ansible-que-es-awx-instalacion-configuracion-playbooks-para-windows-y-linux-y-mucho-mas/) en donde se explicaba cómo instalar AWX a través de docker.

En esta ocasión, a mi me gustaria profundizar un poco mas y ver el paso a paso de cómo seria la instalación sobre CentOS 7, por ejemplo.

### 1) Requisitos del servidor

* CentOS 7
* 2GB de memoria
* 1 vCPU
* 20GB de espacio en disco

Verificamos la configuración SElinux y que esté en modo permisivo:

```
[root@localhost ~]# sestatus
SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   permissive
Mode from config file:          permissive
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      28
[root@localhost ~]#

```

**Watch out!** Se puede modificar con el fichero `/etc/selinux/config`

Editamos el fichero de hosts `/etc/hosts` para que se resuelva a si mismo:

```
[root@localhost ~]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.1.150   ansible-awx
```

Habilitamos el firewall:

```
[root@localhost ~]# systemctl enable firewalld
[root@localhost ~]# systemctl start firewalld
[root@localhost ~]# firewall-cmd --add-service=http --permanent;firewall-cmd --add-service=https --permanent
success
success
[root@localhost ~]# systemctl restart firewalld
```


![ps6-0]({{ site.imagesposts2019 }}/01/PowerShell6-0.png)


https://galaxy.ansible.com/geerlingguy/awx/

http://khmel.org/?p=1245

https://www.howtoforge.com/tutorial/centos-ansible-awx-installation/




Un saludo!

Miquel.


