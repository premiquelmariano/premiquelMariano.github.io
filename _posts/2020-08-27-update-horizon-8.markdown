---
title: Actualizar Horizon 7.x a Horizon 8 (2006)
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
permalink: /jmp-part18/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-1-introduction/

https://www.ageroskam.nl/vmware/jmp-installing-and-configuring-part-one/

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

# Instalación y configuración JMP Server

![update01]({{ site.imagesposts2020 }}/08/update01.png){: .align-center}
![update02]({{ site.imagesposts2020 }}/08/update02.png){: .align-center}
![update03]({{ site.imagesposts2020 }}/08/update03.png){: .align-center}
![update04]({{ site.imagesposts2020 }}/08/update04.png){: .align-center}
![update05]({{ site.imagesposts2020 }}/08/update05.png){: .align-center}
![update06]({{ site.imagesposts2020 }}/08/update06.png){: .align-center}
![update07]({{ site.imagesposts2020 }}/08/update07.png){: .align-center}
![update08]({{ site.imagesposts2020 }}/08/update08.png){: .align-center}
![update09]({{ site.imagesposts2020 }}/08/update09.png){: .align-center}
![update10]({{ site.imagesposts2020 }}/08/update10.png){: .align-center}
![update11]({{ site.imagesposts2020 }}/08/update11.png){: .align-center}
![update12]({{ site.imagesposts2020 }}/08/update12.png){: .align-center}
![update13]({{ site.imagesposts2020 }}/08/update13.png){: .align-center}
![update14]({{ site.imagesposts2020 }}/08/update14.png){: .align-center}
![update15]({{ site.imagesposts2020 }}/08/update15.png){: .align-center}
![update16]({{ site.imagesposts2020 }}/08/update16.png){: .align-center}
![update17]({{ site.imagesposts2020 }}/08/update17.png){: .align-center}
![update18]({{ site.imagesposts2020 }}/08/update18.png){: .align-center}
![update19]({{ site.imagesposts2020 }}/08/update19.png){: .align-center}
![update20]({{ site.imagesposts2020 }}/08/update20.png){: .align-center}
![update21]({{ site.imagesposts2020 }}/08/update21.png){: .align-center}
![update22]({{ site.imagesposts2020 }}/08/update22.png){: .align-center}
![update23]({{ site.imagesposts2020 }}/08/update23.png){: .align-center}
![update24]({{ site.imagesposts2020 }}/08/update24.png){: .align-center}
![update25]({{ site.imagesposts2020 }}/08/update25.png){: .align-center}
![update26]({{ site.imagesposts2020 }}/08/update26.png){: .align-center}
![update27]({{ site.imagesposts2020 }}/08/update27.png){: .align-center}
![update28]({{ site.imagesposts2020 }}/08/update28.png){: .align-center}
![update29]({{ site.imagesposts2020 }}/08/update29.png){: .align-center}
![update30]({{ site.imagesposts2020 }}/08/update30.png){: .align-center}
![update31]({{ site.imagesposts2020 }}/08/update31.png){: .align-center}
![update32]({{ site.imagesposts2020 }}/08/update32.png){: .align-center}
![update33]({{ site.imagesposts2020 }}/08/update33.png){: .align-center}
![update34]({{ site.imagesposts2020 }}/08/update34.png){: .align-center}
![update35]({{ site.imagesposts2020 }}/08/update35.png){: .align-center}
![update36]({{ site.imagesposts2020 }}/08/update36.png){: .align-center}
![update37]({{ site.imagesposts2020 }}/08/update37.png){: .align-center}



Espero que os sirva.

Un saludo!

Miquel.


