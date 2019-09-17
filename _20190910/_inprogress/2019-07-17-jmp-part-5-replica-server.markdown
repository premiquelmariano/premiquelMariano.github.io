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
permalink: /jmp-part5/

---

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

# Instalación de un Réplica Server


![replica1]({{ site.imagesposts2019 }}/09/replica1.png){: .align-center}
![replica2]({{ site.imagesposts2019 }}/09/replica2.png){: .align-center}
![replica3]({{ site.imagesposts2019 }}/09/replica3.png){: .align-center}
![replica4]({{ site.imagesposts2019 }}/09/replica4.png){: .align-center}
![replica5]({{ site.imagesposts2019 }}/09/replica5.png){: .align-center}
![replica6]({{ site.imagesposts2019 }}/09/replica6.png){: .align-center}
![replica7]({{ site.imagesposts2019 }}/09/replica7.png){: .align-center}
![replica8]({{ site.imagesposts2019 }}/09/replica8.png){: .align-center}
![replica9]({{ site.imagesposts2019 }}/09/replica9.png){: .align-center}
![replica10]({{ site.imagesposts2019 }}/09/replica10.png){: .align-center}

repadmin.exe /showrepl localhost:389 DC=vdi,DC=vmware,DC=int

repadmin.exe /replicate localhost-FQDN:389 remote-host-FQDN:389 dc=vdi,dc=vmware,dc=int

https://kb.vmware.com/s/article/1021805

![replica11]({{ site.imagesposts2019 }}/09/replica11.png){: .align-center}

Espero que os sirva.

Nos vemos en el próximo post: [Part 6: Instalación y configuración de Security Server]({{ site.url }}/jmp-part6/)

Un saludo!

Miquel.


