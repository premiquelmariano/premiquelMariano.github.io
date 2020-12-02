---
title: Creando un entorno JMP con VMware Horizon - Primeros pasos con DEM
date: '2020-12-02 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
permalink: /jmp-part16/

---

Tras mas de 1 año desde la [primera entrada]({{ site.url }}/jmp-part1/) de esta serie, hoy vamos a ver la última entrega de cómo configurar cuales son los primeros pasos en nuestro entorno DEM. Os dejo aquí el índice de toda la serie:

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server (opcional)]({{ site.url }}/jmp-part5/)
- [Part 6: Instalación y configuración de UAG (opcional)]({{ site.url }}/jmp-part6/)
- [Part 7: Configuración de UAG en HA]({{ site.url }}/jmp-part7/)
- Part 8: Instalación certificado (opcional)
- [Part 9: Preparar plantilla master para Instant Clone]({{ site.url }}/jmp-part9/)
- [Part 10: Configurar un pool de Instant Clone]({{ site.url }}/jmp-part10/)
- [Part 11: Instalar App Volumes]({{ site.url }}/jmp-part11/)
- [Part 12: Configuración inicial App Volumes]({{ site.url }}/jmp-part12/)
- [Part 13: Crear nuestro primer App Stack]({{ site.url }}/jmp-part13/)
- [Part 14: Trabajando con Writable Volumes]({{ site.url }}/jmp-part14/)
- [Part 15: Instalación Dynamic Environment Manager]({{ site.url }}/jmp-part15/)
- [Part 16: Primeros pasos con DEM]({{ site.url }}/jmp-part16/)

# Instalación Dynamic Environment Manager console

Para poder administrar nuestro entorno DEM, lo primero que haremos será instalar la "Management Console".
El instalador para la management console es el mismo que utilizamos para instalar el agente en el [post anterior]({{ site.url }}/jmp-part15/).

![dem-primeros-pasos-00]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-00.png){: .align-center}
![dem-primeros-pasos-01]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-01.png){: .align-center}
![dem-primeros-pasos-02]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-02.png){: .align-center}
![dem-primeros-pasos-03]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-03.png){: .align-center}
![dem-primeros-pasos-04]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-04.png){: .align-center}
![dem-primeros-pasos-05]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-05.png){: .align-center}
![dem-primeros-pasos-06]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-06.png){: .align-center}

# Configuración inicial

Tras instalar la management console y ejecutarla por primera vez, lo primero que nos preguntará es una ruta UNC para guardar la configuración. Esta ruta, ya vimos cómo crearla y que permisos asignarle, también en el [post anterior]({{ site.url }}/jmp-part15/).

![dem-primeros-pasos-07]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-07.png){: .align-center}

Cómo en la ruta, inicialmente no hay ningún tipo de información, nos aparecerá la opción de "Easy Start", este botón, lo que hará es crear toda la estructura y ficheros necesarios para que DEM funcione.

![dem-primeros-pasos-08]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-08.png){: .align-center}
![dem-primeros-pasos-09]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-09.png){: .align-center}
![dem-primeros-pasos-10]({{ site.imagesposts2020 }}/12/dem-primeros-pasos-10.png){: .align-center}


# Pestaña personalization

# Pestaña User Environment

# Pestaña Computer Environment

# Pestaña Condition Sets

# Pestaña Application Migration



Espero que os sirva.

Un saludo!

Miquel.


