---
title: Creando un entorno JMP con VMware Horizon - Parte 11 - Instalar App Volumes
date: '2019-07-17 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
permalink: /jmp-part11/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-6-installing-app-volumes/

Buenos dias a tod@s!!

En la siguiente serie de posts, pretendo explicar durante las próximas semanas el paso a paso para instalar un entorno JMP (Just-in-Time Management Platform) utilizando VMware Horizon 7 Instant Clones + App Volumes + VMware UEM (User Environment Manager) 

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server]({{ site.url }}/jmp-part5/)
- [Part 6: Intalación y configuración de Security Server]({{ site.url }}/jmp-part6/)
- [Part 7: Intalación y configuración de UAG]({{ site.url }}/jmp-part7/)
- [Part 8: Instalación certificado (opcional)]({{ site.url }}/jmp-part8/)
- [Part 9: Preparar plantilla master para Instant Clone]({{ site.url }}/jmp-part9/)
- [Part 10: Configurar un pool de Instant Clone]({{ site.url }}/jmp-part10/)
- [Part 11: Instalar App Volumes]({{ site.url }}/jmp-part11/)
- [Part 12: Configuración inicial App Volumes]({{ site.url }}/jmp-part12/)
- [Part 13: Crear nuestro primer App Stack]({{ site.url }}/jmp-part13/)
- [Part 14: Trabajando con Writable Volumes]({{ site.url }}/jmp-part14/)
- [Part 15: User Environment Manager Installation]({{ site.url }}/jmp-part15/)
- [Part 16: Primeros pasos con UEM]({{ site.url }}/jmp-part16/)
- [Part 17: Instalación y configuración JMP Server]({{ site.url }}/jmp-part17/)
- [Part 18: Aprovisionamiento con JMP]({{ site.url }}/jmp-part18/)

# Requisitos del servidor

Para la instalación del servidor de App Volumes, necesitaremos una máquina con las siguientes especificaciones:

### Hardware:

- 4 vCPU
- 2Gb RAM
- 20Gb Disco

### Software

- Windows Server 2008 R2, 2012 R2, 2016 o 2019 (Standard o Datacenter)
- Un servidor de BBDD MS SQL Server 2012 SP1 o 2017 (puede ser express)

# Crear usuario de servicio en nuestro directorio activo

![appvol01]({{ site.imagesposts2020 }}/01/appvol01.png){: .align-center}
![appvol02]({{ site.imagesposts2020 }}/01/appvol02.png){: .align-center}
![appvol03]({{ site.imagesposts2020 }}/01/appvol03.png){: .align-center}
![appvol04]({{ site.imagesposts2020 }}/01/appvol04.png){: .align-center}
![appvol05]({{ site.imagesposts2020 }}/01/appvol05.png){: .align-center}
![appvol06]({{ site.imagesposts2020 }}/01/appvol06.png){: .align-center}
![appvol07]({{ site.imagesposts2020 }}/01/appvol07.png){: .align-center}
![appvol08]({{ site.imagesposts2020 }}/01/appvol08.png){: .align-center}
![appvol09]({{ site.imagesposts2020 }}/01/appvol09.png){: .align-center}
![appvol10]({{ site.imagesposts2020 }}/01/appvol10.png){: .align-center}
![appvol11]({{ site.imagesposts2020 }}/01/appvol11.png){: .align-center}
![appvol12]({{ site.imagesposts2020 }}/01/appvol12.png){: .align-center}
![appvol13]({{ site.imagesposts2020 }}/01/appvol13.png){: .align-center}


# Agregar permisos al usuario en nuestro vCenter

# Crear usuario para la BBDD

https://www.ageroskam.nl/app-volumes/install-and-configure-vmware-app-volumes-manager/

# Instalación de App Volumes


Espero que os sirva.

Un saludo!

Miquel.


