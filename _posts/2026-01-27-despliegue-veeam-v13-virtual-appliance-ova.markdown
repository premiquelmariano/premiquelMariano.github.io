---
title: Instalación Veeam Backup & Replication v13
subtitle: Depliegue nuevo virtual appliance
date: '2026-01-20 00:00:00'
layout: post
thumbnail-img: https://miquelmariano.github.io/assets/images/posts/2026/01/primera-vm-01.png
cover-img: https://miquelmariano.github.io/assets/images/fondos/03.jpg
share-img: https://miquelmariano.github.io/assets/images/posts/2026/01/primera-vm-01.png
published: true
author: Miquel Mariano
tag:
- veeam
- backup
- ramsonware
---

Cómo muchos ya sabréis, el pasado mes de septiembre Veeam lanzó la versión 13 de su producto estrella Veeam Backup & Replication.

Este lanzamiento marca uno de los mayores cambios en el producto con la introducción de una versión appliance basada en Linux como forma principal de despliegue, además de la opción tradicional Windows.

# Puntos clave de Veeam v13

1. Nuevo enfoque: appliance Linux (Veeam Software Appliance)
- Veeam deja gradualmente la necesidad de Windows Server para el backup core, ofreciendo una appliance Linux preconfigurada y endurecida (JeOS) para mayor seguridad y simplicidad. 
- Se distribuye en ISO y OVA para entornos físicos y virtuales. 

2. Seguridad reforzada
- Hardened by default: SELinux, servicios mínimos, actualizaciones automatizadas y menor superficie de ataque. 
- Integración con SSO (SAML), RBAC avanzado y detección mejorada de amenazas. 

3. Interfaz moderna
-  Nueva consola web HTTPS para gestión moderna y accesible desde navegador, junto con compatibilidad con roles y SSO. 

4. Operaciones y resiliencia
- Alta disponibilidad nativa planeada en appliance. 
- Automatización de despliegue y menor mantenimiento OS. 

5. Mejoras ampliadas de plataforma
- Seguridad y protección avanzada: detección de malware, inmutabilidad por defecto y análisis inteligente. 
- Cloud y recuperación: recuperación instantánea a Microsoft Azure y mejoras de integración cloud. 
- Performance y escalabilidad: arquitectura 64-bit, mejoras en engine y más paralelismo. 

# Nuestra primera VM

Arrancaremos el asistente de despliegue de una nueva instancia desde el menú de "Provisioning" >> "Add"

![HPE_Morpheus_VM_Essentials_primera-vm-01]({{ site.imagesposts2026 }}/01/primera-vm-01.png){: .mx-auto.d-block :}

Seleccionaremos qué tipo de instancia vamos a desplegar; en nuestro caso desplegaremos sobre un cluster HVM

![HPE_Morpheus_VM_Essentials_primera-vm-02]({{ site.imagesposts2026 }}/01/primera-vm-02.png){: .mx-auto.d-block :}

Completamos información básica de la instancia, como nombre, grupo, en qué cloud desplegaremos, etc etc...

![HPE_Morpheus_VM_Essentials_primera-vm-03]({{ site.imagesposts2026 }}/01/primera-vm-03.png){: .mx-auto.d-block :}

Aquí es donde definiremos el "sabor" de la instancia, el tamaño y número de discos, su ubicación en los datastores, la red, la iso, etc etc

![HPE_Morpheus_VM_Essentials_primera-vm-04]({{ site.imagesposts2026 }}/01/primera-vm-04.png){: .mx-auto.d-block :}

En las opciones avanzadas es importante conectar las VirtIO para poder instalar el driver durante la instalación, de lo contrario, Windows será incapaz de detectar el disco para realizar la instalación.

![HPE_Morpheus_VM_Essentials_primera-vm-05]({{ site.imagesposts2026 }}/01/primera-vm-05.png){: .mx-auto.d-block :}

Seguiremos hasta llegar al final del asistente.

![HPE_Morpheus_VM_Essentials_primera-vm-06]({{ site.imagesposts2026 }}/01/primera-vm-06.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-07]({{ site.imagesposts2026 }}/01/primera-vm-07.png){: .mx-auto.d-block :}

Una vez arrancado el despliegue, en la pestaña de histórico podremos ver el paso a paso del proceso que se está llevando a cabo.

![HPE_Morpheus_VM_Essentials_primera-vm-08]({{ site.imagesposts2026 }}/01/primera-vm-08.png){: .mx-auto.d-block :}

A partir de aquí, abriremos la consola de la instancia y realizaremos la instalación de Windows Server.

![HPE_Morpheus_VM_Essentials_primera-vm-09]({{ site.imagesposts2026 }}/01/primera-vm-09.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-10]({{ site.imagesposts2026 }}/01/primera-vm-10.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-11]({{ site.imagesposts2026 }}/01/primera-vm-11.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-12]({{ site.imagesposts2026 }}/01/primera-vm-12.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-13]({{ site.imagesposts2026 }}/01/primera-vm-13.png){: .mx-auto.d-block :}

Veréis que no aparece ningún disco, eso es debido a que los drivers SCSI todavía no están instalados y deberemos cargarlos a través del CD de las VirtIO que previamente hemos conectado a la instancia.

![HPE_Morpheus_VM_Essentials_primera-vm-14]({{ site.imagesposts2026 }}/01/primera-vm-14.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-15]({{ site.imagesposts2026 }}/01/primera-vm-15.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-16]({{ site.imagesposts2026 }}/01/primera-vm-16.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-17]({{ site.imagesposts2026 }}/01/primera-vm-17.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-18]({{ site.imagesposts2026 }}/01/primera-vm-18.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-19]({{ site.imagesposts2026 }}/01/primera-vm-19.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-20]({{ site.imagesposts2026 }}/01/primera-vm-20.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-21]({{ site.imagesposts2026 }}/01/primera-vm-21.png){: .mx-auto.d-block :}

Y ya tendríamos nuestro Windows Server instalado y arrancado.

![HPE_Morpheus_VM_Essentials_primera-vm-22]({{ site.imagesposts2026 }}/01/primera-vm-22.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-23]({{ site.imagesposts2026 }}/01/primera-vm-23.png){: .mx-auto.d-block :}

Finalmente, para que todo sea 100% funcional y dejar la instalación finalizada, tocará instalar las VirtIO. Aquí se incluyen todos los drivers y binarios necesarios para que se reconozca todo el hardware virtual que le está provisionando VM Essentials.

![HPE_Morpheus_VM_Essentials_primera-vm-24]({{ site.imagesposts2026 }}/01/primera-vm-24.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-25]({{ site.imagesposts2026 }}/01/primera-vm-25.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-26]({{ site.imagesposts2026 }}/01/primera-vm-26.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-27]({{ site.imagesposts2026 }}/01/primera-vm-27.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-28]({{ site.imagesposts2026 }}/01/primera-vm-28.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-29]({{ site.imagesposts2026 }}/01/primera-vm-29.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-20]({{ site.imagesposts2026 }}/01/primera-vm-30.png){: .mx-auto.d-block :}
![HPE_Morpheus_VM_Essentials_primera-vm-31]({{ site.imagesposts2026 }}/01/primera-vm-31.png){: .mx-auto.d-block :}

Y hasta aquí por hoy, en entorno ya va cogiendo forma poco a poco y ya tenemos nuestra primera VM desplegada.

Nos vemos en el próximo post ;-)

Un saludo

Miquel.