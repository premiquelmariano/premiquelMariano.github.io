---
title: Creando un entorno JMP con VMware Horizon - Parte 5
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
permalink: /jmp-part9/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-4-connection-server-install-and-initial-configuration/

Buenos dias a tod@s!!

En la siguiente serie de posts, pretendo explicar durante las próximas semanas el paso a paso para instalar un entorno JMP (Just-in-Time Management Platform) utilizando VMware Horizon 7 Instant Clones + App Volumes + VMware UEM (User Environment Manager) 

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server]({{ site.url }}/jmp-part5/)
- [Part 6: Instalación y configuración de Security Server]({{ site.url }}/jmp-part6/)
- [Part 7: Instalación y configuración de UAG]({{ site.url }}/jmp-part7/)
- [Part 8: Insstalación certificado (opcional)]({{ site.url }}/jmp-part8/)
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

# Preparar plantilla master para Instant Clone

Partiremos de la base de que ya hemos elegido nuestro SO base (generalmente un SO cliente) y que ya lo tenemos instalado en nuestra VM que nos servirá como plantilla master.

Como en esta serie de posts estamos tratando de explicar el paso a paso para crear un entorno JMP, necesitaremos instalar varios agentes en nuestra plantilla:

1 VMware Tools
2 VMware Horizon Agent
3 VMware User Environment Manager (UEM) agent
4 VMware App Volumes Agent

En este post, sólo vamos a ver cómo instalar nuestro Horizon Agent, pero hay que tener en cuenta que el orden de instalación de los agentes es importante a la hora de configurar bien nuestra plantilla. Podeis consultar la nota técnica en la [siguiente KB](https://kb.vmware.com/s/article/2118048)
 

![con21]({{ site.imagesposts2019 }}/08/con21.png){: .align-center}

Espero que os sirva.

Nos vemos en el próximo post: [Part 6: Instalación y configuración de Security Server]({{ site.url }}/jmp-part6/)

Un saludo!

Miquel.


