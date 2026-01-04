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


# Documentación

La documentación oficial la podrememos encontrar [aquí](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00006775en_us&docLocale=en_US&page=GUID-9886AD4A-5C64-4E09-A106-B14419362757.html#ariaid-title1)

Por el momento HPE VM Essentials sólo se permite crear el cluster HCI con un único disco por nodo. El resto de discos los deberemos de ayadir al cluster ceph a través de cli y los comandos nativos ceph

En un futuro se espera poder seleccionar mas discos.

# Laboratorio

En este laboratorio tenemos como base 3 nodos VME [aquí teneis el post para su instalación](https://miquelmariano.github.io/2025/10/17/instalacion-nodo-vme/).
Y cada uno de ellos con un disco adicional de 150Gb que será el que nos aportará la capacidad al cluster Ceph

![HPE_Morpheus_VM_Essentials_ceph-cluster-01]({{ site.imagesposts2025 }}/12/ceph-01.png){: .mx-auto.d-block :}

Arrancamos el asistente para agregar nuevo cluster de HVM

![HPE_Morpheus_VM_Essentials_ceph-cluster-02]({{ site.imagesposts2025 }}/12/ceph-02.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-03]({{ site.imagesposts2025 }}/12/ceph-03.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-04]({{ site.imagesposts2025 }}/12/ceph-04.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-05]({{ site.imagesposts2025 }}/12/ceph-05.png){: .mx-auto.d-block :}

En este punto, en el desplegable seleccionaremos la opción de cluster HCI Ceph y añadiremos los 3 hosts mínimos necesarios para su creación.

![HPE_Morpheus_VM_Essentials_ceph-cluster-06]({{ site.imagesposts2025 }}/12/ceph-06.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-07]({{ site.imagesposts2025 }}/12/ceph-07.png){: .mx-auto.d-block :}

Veremos como arranca el proceso de aprovisionamiento y en el submenú de history iremos viendo todo el proceso

![HPE_Morpheus_VM_Essentials_ceph-cluster-08]({{ site.imagesposts2025 }}/12/ceph-08.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-09]({{ site.imagesposts2025 }}/12/ceph-09.png){: .mx-auto.d-block :}

Desplegando cada uno de los nodos, podremos ir viendo las operaciones que se están realizando y en caso de algún error, nos será muy cómodo analizar la posible causa

![HPE_Morpheus_VM_Essentials_ceph-cluster-10]({{ site.imagesposts2025 }}/12/ceph-10.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-11]({{ site.imagesposts2025 }}/12/ceph-11.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-12]({{ site.imagesposts2025 }}/12/ceph-12.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-13]({{ site.imagesposts2025 }}/12/ceph-13.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-14]({{ site.imagesposts2025 }}/12/ceph-14.png){: .mx-auto.d-block :}

![HPE_Morpheus_VM_Essentials_ceph-cluster-15]({{ site.imagesposts2025 }}/12/ceph-15.png){: .mx-auto.d-block :}

Una vez finalizado el despliegue, nos aparecerá como disponible un nuevo clúster de computo del tipo HCI Ceph

![HPE_Morpheus_VM_Essentials_ceph-cluster-16]({{ site.imagesposts2025 }}/12/ceph-16.png){: .mx-auto.d-block :}

Y ya veremos nuestro RBD Pool con la suma de los 3 nodos (150Gb por nodo)

![HPE_Morpheus_VM_Essentials_ceph-cluster-17]({{ site.imagesposts2025 }}/12/ceph-17.png){: .mx-auto.d-block :}

# Comandos útiles ceph

En [este post](https://www.redhat.com/en/blog/10-commands-every-ceph-administrator-should-know) de la misma comunidad redhat he encontrado algunos comandos interesantes para validar el buen estado de salud del cluster

Ver estado de salud global del cluster
`ceph status || ceph -w`
![HPE_Morpheus_VM_Essentials_ceph-cluster-18]({{ site.imagesposts2025 }}/12/ceph-18.png){: .mx-auto.d-block :}

Ver el espacio libre en los diferentes Pools
`ceph df`
![HPE_Morpheus_VM_Essentials_ceph-cluster-19]({{ site.imagesposts2025 }}/12/ceph-19.png){: .mx-auto.d-block :}

Ver el estado de los discos y el host que los aporta
`ceph osd tree`
![HPE_Morpheus_VM_Essentials_ceph-cluster-20]({{ site.imagesposts2025 }}/12/ceph-20.png){: .mx-auto.d-block :}

Y hasta aquí por hoy.

Un saludo

Miquel.