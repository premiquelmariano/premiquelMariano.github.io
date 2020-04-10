---
title: Creando un entorno JMP con VMware Horizon - Parte 14
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
permalink: /jmp-part14/

---

Siguiendo con la serie de posts sobre VMware Horizon 7 y JMP, hoy vamos a seguir hablando sobre App Volumes, en concreto, de los Writable Volumes.

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

#	¿Qué es Writable Volumes?

Sacado de la documentación oficial, los Writable Volumes, son volúmenes dónde los usuarios pueden guardar sus propios datos y configuraciones específicos de su perfil. Este volúmen se asigna a cada usuario y los datos que ahí se almacenan se migran con el usuario en las diferentes máquinas donde se inicie sesión.

![writable_volumes001]({{ site.imagesposts2020 }}/04/writable_volumes001.png){: .align-center}

#	¿Para qué se usan los Writable Volumes?

https://docs.vmware.com/en/VMware-App-Volumes/2.12/com.vmware.appvolumes.user.doc/GUID-EF439E8C-E102-4ECD-A9F5-BA1280FDFD83.html

#	Diferentes perfiles de Writable Volumes

https://ageroskam.nl/app-volumes-2-x/manage-user-profiles-with-writable-volumes/

#	Creación de Writable Volumes

http://www.virtualizationblog.com/managing-user-installed-applications-user-profile-using-vmware-app-volumes/

![writable_volumes000]({{ site.imagesposts2020 }}/04/writable_volumes000.png){: .align-center}

![writable_volumes002]({{ site.imagesposts2020 }}/04/writable_volumes002.png){: .align-center}
![writable_volumes003]({{ site.imagesposts2020 }}/04/writable_volumes003.png){: .align-center}
![writable_volumes004]({{ site.imagesposts2020 }}/04/writable_volumes004.png){: .align-center}
![writable_volumes005]({{ site.imagesposts2020 }}/04/writable_volumes005.png){: .align-center}
![writable_volumes006]({{ site.imagesposts2020 }}/04/writable_volumes006.png){: .align-center}
![writable_volumes007]({{ site.imagesposts2020 }}/04/writable_volumes007.png){: .align-center}

#	¿Cómo editar un template de Writable Volumes?

https://ageroskam.nl/app-volumes-2-x/manage-user-profiles-with-writable-volumes/




Un saludo!

Miquel.


