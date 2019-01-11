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

Habilitamos el repositorio EPEL para CentOS7:

```
[root@localhost ~]# yum install -y epel-release
Complementos cargados:fastestmirror
base                                                                                                                                                          | 3.6 kB  00:00:00
extras                                                                                                                                                        | 3.4 kB  00:00:00
updates                                                                                                                                                       | 3.4 kB  00:00:00
(1/4): base/7/x86_64/group_gz                                                                                                                                 | 166 kB  00:00:00
(2/4): extras/7/x86_64/primary_db                                                                                                                             | 156 kB  00:00:00
(3/4): updates/7/x86_64/primary_db                                                                                                                            | 1.3 MB  00:00:00
(4/4): base/7/x86_64/primary_db                                                                                                                               | 6.0 MB  00:00:05
Determining fastest mirrors
 * base: centos.uvigo.es
 * extras: centos.uvigo.es
 * updates: ftp.rediris.es
Resolviendo dependencias
--> Ejecutando prueba de transacción
---> Paquete epel-release.noarch 0:7-11 debe ser instalado
--> Resolución de dependencias finalizada

Dependencias resueltas

=====================================================================================================================================================================================
 Package                                         Arquitectura                              Versión                                   Repositorio                               Tamaño
=====================================================================================================================================================================================
Instalando:
 epel-release                                    noarch                                    7-11                                      extras                                     15 k

Resumen de la transacción
=====================================================================================================================================================================================
Instalar  1 Paquete

Tamaño total de la descarga: 15 k
Tamaño instalado: 24 k
Downloading packages:
advertencia:/var/cache/yum/x86_64/7/extras/packages/epel-release-7-11.noarch.rpm: EncabezadoV3 RSA/SHA256 Signature, ID de clave f4a80eb5: NOKEY
No se ha instalado la llave pública de epel-release-7-11.noarch.rpm
epel-release-7-11.noarch.rpm                                                                                                                                  |  15 kB  00:00:00
Obteniendo clave desde file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importando llave GPG 0xF4A80EB5:
 Usuarioid  : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Huella       : 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Paquete    : centos-release-7-4.1708.el7.centos.x86_64 (@anaconda)
 Desde      : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Instalando    : epel-release-7-11.noarch                                                                                                                                       1/1
  Comprobando   : epel-release-7-11.noarch                                                                                                                                       1/1

Instalado:
  epel-release.noarch 0:7-11

¡Listo!
[root@localhost ~]#
```




![ps6-0]({{ site.imagesposts2019 }}/01/PowerShell6-0.png)


https://galaxy.ansible.com/geerlingguy/awx/

http://khmel.org/?p=1245

https://www.howtoforge.com/tutorial/centos-ansible-awx-installation/




Un saludo!

Miquel.


