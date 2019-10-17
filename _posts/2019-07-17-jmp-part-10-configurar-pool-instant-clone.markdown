---
title: Creando un entorno JMP con VMware Horizon - Parte 10 - Configurar un pool de Instant Clone
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
permalink: /jmp-part10/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-4-connection-server-install-and-initial-configuration/

Buenos días a tod@s!!

En la siguiente serie de posts, pretendo explicar durante las próximas semanas el paso a paso para instalar un entorno JMP (Just-in-Time Management Platform) utilizando VMware Horizon 7 Instant Clones + App Volumes + VMware UEM (User Environment Manager) 

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server]({{ site.url }}/jmp-part5/)
- [Part 6: Instalación y configuración de Security Server]({{ site.url }}/jmp-part6/)
- [Part 7: Instalación y configuración de UAG]({{ site.url }}/jmp-part7/)
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

# Tecnología Instant clone

Antes de empezar a ver cómo crear un pool de Instant Clone, me gustaria hacer un pequeño inciso en qué es y cómo funciona esta tecnología de Instant Clone.

Mi amigo [Ricard Ibañez](https://www.cenabit.com/) escribió un fantástico capítulo en le libro [#VmwarePorvExperts](https://miquelmariano.github.io/vmwareporvexperts/) dónde explica con detalle esta tecnología. Os animo a que le echeis un vistazo.

**Instant Clone.** La tecnología Instant Clone es muy parecida en concepto a Linked Clone, pero con una operativa totalmente distinta. Así como Linked Clone opera a nivel de disco y mantiene un disco en cada escritorio virtual con los datos diferenciales respecto a la VM Réplica, Instant Clone genera en cada escritorio virtual, un disco diferencial y una memoria RAM diferencial respecto a una VM Parent, que se aprovisiona para cada uno de los nodos ESXi y se mantiene encendida.


![ic01]({{ site.imagesposts2019 }}/10/ic01.png){: .align-center}

![ic02]({{ site.imagesposts2019 }}/10/ic02.png){: .align-center}

# Configurar un pool de Instant Clone


![pool-ic01]({{ site.imagesposts2019 }}/10/pool-ic01.png){: .align-center}
![pool-ic02]({{ site.imagesposts2019 }}/10/pool-ic02.png){: .align-center}
![pool-ic03]({{ site.imagesposts2019 }}/10/pool-ic03.png){: .align-center}
![pool-ic04]({{ site.imagesposts2019 }}/10/pool-ic04.png){: .align-center}
![pool-ic05]({{ site.imagesposts2019 }}/10/pool-ic05.png){: .align-center}
![pool-ic06]({{ site.imagesposts2019 }}/10/pool-ic06.png){: .align-center}
![pool-ic07]({{ site.imagesposts2019 }}/10/pool-ic07.png){: .align-center}
![pool-ic08]({{ site.imagesposts2019 }}/10/pool-ic08.png){: .align-center}
![pool-ic09]({{ site.imagesposts2019 }}/10/pool-ic09.png){: .align-center}
![pool-ic10]({{ site.imagesposts2019 }}/10/pool-ic10.png){: .align-center}
![pool-ic11]({{ site.imagesposts2019 }}/10/pool-ic11.png){: .align-center}
![pool-ic12]({{ site.imagesposts2019 }}/10/pool-ic12.png){: .align-center}


Y hasta aquí por hoy, en el próximo post veremos cómo crear nuestro primer Pool de Linked Clones

Espero que os sirva.

Nos vemos en el próximo post: [Part 11: Instalar App Volumes]({{ site.url }}/jmp-part11/)

Un saludo!

Miquel.


