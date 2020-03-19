---
title: Creando un entorno JMP con VMware Horizon - Parte 13
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
permalink: /jmp-part13/

---

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

Si habeis seguido la serie con atención, en este punto ya tendreis [instalado]({{ site.url }}/jmp-part11/) y [configurado]({{ site.url }}/jmp-part12/) vuestro entorno con App Volumes.

Es el momento ahora de ver cómo se crea nuestro primer AppStack.

Un AppStack es un disco, generalmente un .vmdk, de sólo lectura que contiene una o múltiples aplicaciones ya instaladas. Estos AppStack los podremos asignar a usuarios, unidades organizativas (OU), cuantas de equipo, etc, etc.. con el fin de permitir la entrega y uso de estas aplicaciones a nuestros usuarios finales.

Es posible combinar diferentes aplicaciones en un mismo AppStack, lo que nos permitirá agrupar, por ejemplo, las aplicaciones "core" de nuestra empresa y distribuirlas conjuntamente.

Una vez tengamos creados los AppStack, se montarán en modo sólo lectura y serán compartidos entre los escritorios de nuestros usuarios dentro del datacenter.

Vamos al lio!

Al entrar en nuestro App Volumes Manager, nos dirigiremos en la pestaña "Volumes" > "AppStacks" y pulsaremos sobre el botón "Create"

![appstack1]({{ site.imagesposts2019 }}/08/appstack1.png){: .align-center}

Se nos abrirá el menú de creación, en dónde especificaremos los siguientes parámetros:

Name: Nombre descriptivo del AppStack
Storage: Se refiere al datastore en dónde se guardará el disco .vmdk con las aplicaciones instaladas
Path: Hace referencia a la ruta dentro del datastore previamente seleccionado
Template: La plantilla en la que se basará el nuevo .vmdk que crearemos. La plantilla por defecto es de 20Gb y será suficiente para la gran mayoria de aplicaciones.
Description: Por si queremos poner una descripción

![appstack2]({{ site.imagesposts2019 }}/08/appstack2.png){: .align-center}

![appstack3]({{ site.imagesposts2019 }}/08/appstack3.png){: .align-center}

![appstack4]({{ site.imagesposts2019 }}/08/appstack4.png){: .align-center}
![appstack5]({{ site.imagesposts2019 }}/08/appstack5.png){: .align-center}
![appstack6]({{ site.imagesposts2019 }}/08/appstack6.png){: .align-center}
![appstack7]({{ site.imagesposts2019 }}/08/appstack7.png){: .align-center}
![appstack8]({{ site.imagesposts2019 }}/08/appstack8.png){: .align-center}
![appstack9]({{ site.imagesposts2019 }}/08/appstack9.png){: .align-center}
![appstack10]({{ site.imagesposts2019 }}/08/appstack10.png){: .align-center}
![appstack11]({{ site.imagesposts2019 }}/08/appstack11.png){: .align-center}
![appstack12]({{ site.imagesposts2019 }}/08/appstack12.png){: .align-center}
![appstack13]({{ site.imagesposts2019 }}/08/appstack13.png){: .align-center}
![appstack14]({{ site.imagesposts2019 }}/08/appstack14.png){: .align-center}



Espero que os sirva.

Un saludo!

Miquel.


