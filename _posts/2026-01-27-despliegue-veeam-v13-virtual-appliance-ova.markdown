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

# Despliegue virtual appliance en vSphere

![Despliegue-veeam-virtual-appliance-01]({{ site.imagesposts2026 }}/02/veeam-ova-01.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-02]({{ site.imagesposts2026 }}/02/veeam-ova-02.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-03]({{ site.imagesposts2026 }}/02/veeam-ova-03.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-04]({{ site.imagesposts2026 }}/02/veeam-ova-04.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-05]({{ site.imagesposts2026 }}/02/veeam-ova-05.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-06]({{ site.imagesposts2026 }}/02/veeam-ova-06.png){: .mx-auto.d-block :}
![Despliegue-veeam-virtual-appliance-07]({{ site.imagesposts2026 }}/02/veeam-ova-07.png){: .mx-auto.d-block :}

# Configuración inicial

![HPE_Morpheus_VM_Essentials_primera-vm-01]({{ site.imagesposts2026 }}/01/primera-vm-01.png){: .mx-auto.d-block :}

Y hasta aquí por hoy, en entorno ya va cogiendo forma poco a poco y ya tenemos nuestra primera VM desplegada.

Nos vemos en el próximo post ;-)

Un saludo

Miquel.