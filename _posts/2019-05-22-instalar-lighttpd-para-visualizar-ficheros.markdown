---
title: Instalar lighttpd para visualizar ficheros
date: '2018-02-28 00:00:00'
layout: post
image: /assets/images/posts/2019/06/Cisco-and-Ansible-Happy.png
tag:
- devops
- linux
- centos7
- ansible
- cisco

o: "{{"
c: "}}"
---

Hace tiempo os enseñé [cómo hacer backup automático de switches Cisco con Ansible](https://miquelmariano.github.io/2019/06/05/backup-cisco-con-ansible/). Pues bién, en el post de hoy, quiero mostraros el cómo visualizar esta información de forma fácil.

Utilizaremos lighttpd cómo servidor web para mostrar nuestros ficheros de texto a través del navegador.

## Instalar lighttpd | https://www.linuxhelp.com/how-to-install-lighttpd-web-server-on-centos-7
yum install lighttpd -y


## Deshabilitar ipv6 en el fichero de configuración ( /etc/lighttpd/lighttpd.conf)
server.use-ipv6 = "disable"

## Cambiamos el puerto de escucha por defecto
server.port = 81


systemctl start lighttpd
systemctl enable lighttpd


## Habilitar dir-listing en el fichero de configuración
server.dir-listing = "enable"


## Editar mime para mostrar .yml como yaml
vim /etc/lighttpd/conf.d/mime.conf

## Crear link simbolico de ansible en cd /var/www/lighttpd/ | https://kb.iu.edu/d/abbe
ln -s /etc/ansible /var/www/lighttpd/ansible

## Securizar: https://www.cyberciti.biz/tips/lighttpd-setup-a-password-protected-directory-directories.html

vim /etc/lighttpd/lighttpd.conf

server.modules += ( "mod_auth" )

auth.debug = 2
auth.backend = "plain"
auth.backend.plain.userfile = "/root/.lighttpdpassword"

vim /root/.lighttpdpassword

test:test

Espero que os sirva.

Un saludo!

Miquel.


