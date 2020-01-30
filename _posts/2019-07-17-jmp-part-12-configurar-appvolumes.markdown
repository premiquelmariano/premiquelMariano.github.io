---
title: Creando un entorno JMP con VMware Horizon - Parte 12 - Configuración inicial App Volumes Manager
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
permalink: /jmp-part12/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-6-installing-app-volumes/

https://www.ageroskam.nl/app-volumes/install-and-configure-vmware-app-volumes-manager/

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




![appvol_config1]({{ site.imagesposts2020 }}/01/appvol_config1.png){: .align-center}
![appvol_config2]({{ site.imagesposts2020 }}/01/appvol_config2.png){: .align-center}
![appvol_config3]({{ site.imagesposts2020 }}/01/appvol_config3.png){: .align-center}
![appvol_config4]({{ site.imagesposts2020 }}/01/appvol_config4.png){: .align-center}
![appvol_config5]({{ site.imagesposts2020 }}/01/appvol_config5.png){: .align-center}
![appvol_config6]({{ site.imagesposts2020 }}/01/appvol_config6.png){: .align-center}
![appvol_config7]({{ site.imagesposts2020 }}/01/appvol_config7.png){: .align-center}
![appvol_config8]({{ site.imagesposts2020 }}/01/appvol_config8.png){: .align-center}
![appvol_config9]({{ site.imagesposts2020 }}/01/appvol_config9.png){: .align-center}
![appvol_config10]({{ site.imagesposts2020 }}/01/appvol_config10.png){: .align-center}
![appvol_config11]({{ site.imagesposts2020 }}/01/appvol_config11.png){: .align-center}
![appvol_config12]({{ site.imagesposts2020 }}/01/appvol_config12.png){: .align-center}
![appvol_config13]({{ site.imagesposts2020 }}/01/appvol_config13.png){: .align-center}
![appvol_config14]({{ site.imagesposts2020 }}/01/appvol_config14.png){: .align-center}


