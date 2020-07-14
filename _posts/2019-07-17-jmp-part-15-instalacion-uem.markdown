---
title: Creando un entorno JMP con VMware Horizon - Parte 15 - Instalación Dynamic Environment Manager
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
permalink: /jmp-part15/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-1-introduction/

https://www.sistel.es/gestion-del-entorno-del-usuario-horizon-7-uem

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

# Primeros pasos con UEM

A fecha de edición de este post, la última versión disponible es la  9.11, así que nos descargaremos esa versión
![dem_download]({{ site.imagesposts2019 }}/08/dem_download01.png){: .align-center}

En el fichero que nos descargemos, encontraremos una carpeta con unas plantillas .admx y sus correspondientes ficheros de idioma. Tendremos que copiarlos en nuestro DC para poder crear posteriormente las GPO

![uem_config1]({{ site.imagesposts2019 }}/08/uem_config1.png){: .align-center}
![uem_config2]({{ site.imagesposts2019 }}/08/uem_config2.png){: .align-center}
![uem_config3]({{ site.imagesposts2019 }}/08/uem_config3.png){: .align-center}
![uem_config4]({{ site.imagesposts2019 }}/08/uem_config4.png){: .align-center}
![uem_config5]({{ site.imagesposts2019 }}/08/uem_config5.png){: .align-center}
![uem_config6]({{ site.imagesposts2019 }}/08/uem_config6.png){: .align-center}
![uem_config7]({{ site.imagesposts2019 }}/08/uem_config7.png){: .align-center}
![uem_config8]({{ site.imagesposts2019 }}/08/uem_config8.png){: .align-center}
![uem_config9]({{ site.imagesposts2019 }}/08/uem_config9.png){: .align-center}


Espero que os sirva.

Un saludo!

Miquel.


