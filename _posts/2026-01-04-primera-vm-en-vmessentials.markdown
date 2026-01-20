---
title: Creación de nuestra primera VM en HPE VM Essentials
subtitle: Parte 6
date: '2026-01-04 00:00:00'
layout: post
thumbnail-img: https://miquelmariano.github.io/assets/images/posts/2026/01/primera-vm-01.png
cover-img: https://miquelmariano.github.io/assets/images/fondos/02.jpg
share-img: https://miquelmariano.github.io/assets/images/posts/2026/01/primera-vm-01.png
published: true
author: Miquel Mariano
tag:
- kvm
- hpe
- vme
- cloud
- morpheus
- ha
---

Arrancamos el año con una nueva entrada en la serie sobre VM Essentials. En esta ocasión vamos a ver cómo crear nuestra primera VM.

Aprovecho a continuación para recordar el índice de toda la serie.

<details markdown="1">
<summary>VER TODA LA SERIE DE POSTS</summary>
- [Parte 1 - Introducción a HPE Morpheus VM Essentials software](https://miquelmariano.github.io/2025/10/17/introduccion-hpe-morpheus-vm-essentials-software/)
- [Parte 2 - Instalación VM Essentials software](https://miquelmariano.github.io/2025/10/17/instalacion-nodo-vme/)
- [Parte 3 - Instalación VME Manager](https://miquelmariano.github.io/2025/11/07/instalacion-manager/)
- [Parte 4 - Configuración inicial](https://miquelmariano.github.io/2025/11/20/configuracion-inicial-primeros-pasos-vm-essentials)
- [Parte 5 - Creación cluster Ceph](https://miquelmariano.github.io/2025/11/20/primera-vm-en-vmessentials)
- [Parte 6 - Desplegar nuestra primera VM]
- [Parte 7 - Backups]
- [Parte 8 - Pruebas de HA]
- [Parte 9 - Migración de VMs desde vSphere]
- [Parte 10 - Comandos útiles]
</details>

# Nuestra primera VM

Arrancaremos el asistente de despliegue de una nueva instancia desde el menú de "Provisioning" >> "Add"

![HPE_Morpheus_VM_Essentials_primera-vm-01]({{ site.imagesposts2026 }}/01/primera-vm-01.png){: .mx-auto.d-block :}

Seleccionaremos que timpo de instancia vamos a desplegar, en nuestro caso desplegaremos sobre un cluster HVM

![HPE_Morpheus_VM_Essentials_primera-vm-02]({{ site.imagesposts2026 }}/01/primera-vm-02.png){: .mx-auto.d-block :}

Completamos información básica de la instancia, como nombre, grupo, en que cloud desplegaremos, etc etc...
![HPE_Morpheus_VM_Essentials_primera-vm-03]({{ site.imagesposts2026 }}/01/primera-vm-03.png){: .mx-auto.d-block :}

Aquí es donde definiremos el "sabor" de la instancia, el tamaño y número de discos, su ubicación en los datastores, la red, la iso, etc etc

![HPE_Morpheus_VM_Essentials_primera-vm-04]({{ site.imagesposts2026 }}/01/primera-vm-04.png){: .mx-auto.d-block :}

En las opciones avanzadas es importante conectar las VirtIO para poder instalar el driver durante la instalación, de lo contrario, Windows será incapaz de detectar el disco para realizar la instalación

![HPE_Morpheus_VM_Essentials_primera-vm-05]({{ site.imagesposts2026 }}/01/primera-vm-05.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-06]({{ site.imagesposts2026 }}/01/primera-vm-06.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-07]({{ site.imagesposts2026 }}/01/primera-vm-07.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-08]({{ site.imagesposts2026 }}/01/primera-vm-08.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-09]({{ site.imagesposts2026 }}/01/primera-vm-09.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-10]({{ site.imagesposts2026 }}/01/primera-vm-10.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-11]({{ site.imagesposts2026 }}/01/primera-vm-11.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-12]({{ site.imagesposts2026 }}/01/primera-vm-12.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-13]({{ site.imagesposts2026 }}/01/primera-vm-13.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-14]({{ site.imagesposts2026 }}/01/primera-vm-14.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-15]({{ site.imagesposts2026 }}/01/primera-vm-15.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-16]({{ site.imagesposts2026 }}/01/primera-vm-16.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-17]({{ site.imagesposts2026 }}/01/primera-vm-17.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-18]({{ site.imagesposts2026 }}/01/primera-vm-18.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-19]({{ site.imagesposts2026 }}/01/primera-vm-19.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-20]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_primera-vm-21]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-22]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-23]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-24]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-25]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-26]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-27]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-28]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-29]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-20]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-31]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}

Y hasta aquí por hoy.

Un saludo

Miquel.