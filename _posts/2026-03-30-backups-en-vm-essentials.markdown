---
title: Backups nativos en VM Essentials
subtitle: Modulo integrado de protección
date: '2026-03-30 00:00:00'
layout: post
thumbnail-img: https://miquelmariano.github.io/assets/images/posts/2026/02/updates-01.png
cover-img: https://miquelmariano.github.io/assets/images/fondos/05.jpg
share-img: https://miquelmariano.github.io/assets/images/posts/2026/01/updates-01.png
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

Seguimos avanzando con la serie de posts sobre HPE VM Essentials. Una parte importante al desplegar nuestras infraestructuras virtuales es contemplar los mecanismos de protección y copia de seguridad que vamos a implementar para dar continuidad a nuestros servicios.

En este post vamos a ver cómo HPE VM Essentials implementa de forma nativa herramientas de backup tanto para el VME Manager como para las propias VMs alojadas en la infraestructura.

<details markdown="1">
<summary>VER TODA LA SERIE DE POSTS</summary>
- [Parte 1 - Introducción a HPE Morpheus VM Essentials software](https://miquelmariano.github.io/introduccion-hpe-morpheus-vm-essentials-software/)
- [Parte 2 - Instalación VM Essentials software](https://miquelmariano.github.io/instalacion-nodo-vme/)
- [Parte 3 - Instalación VME Manager](https://miquelmariano.github.io/instalacion-manager/)
- [Parte 4 - Configuración inicial](https://miquelmariano.github.io/configuracion-inicial-primeros-pasos-vm-essentials)
- [Parte 5 - Creación cluster Ceph](https://miquelmariano.github.io/cluster-ceph/)
- [Parte 6 - Desplegar nuestra primera VM](https://miquelmariano.github.io/primera-vm-en-vmessentials/)
- [Parte 7 - Backups]
- [Parte 8 - Pruebas de HA]
- [Parte 9 - Migración de VMs desde vSphere]
- [Parte 10 - Comandos útiles]
- [Parte 11 - Gestión de actualizaciones en HPE VM Essentials](https://miquelmariano.github.io/actualizaciones-vme-manager-y-nodos-hvm)
</details>

# Backup de VME manager

Antes de nada, os recomiento que le equeis un vistazo a [la documentación oficial tanto para hacer backups como los restores](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007322en_us&page=GUID-1E710344-0932-4A51-B605-18AEF716E46F.html)

Empezamos por la parte más sencilla: proteger el propio Manager. La configuración de Morpheus se almacena en una base de datos MySQL, y el proceso de backup consiste básicamente en un dump de esa BBDD.

Por defecto, si no tenemos ningún repositorio externo configurado, el sistema nos avisará desde el menú principal y los backups se guardarán en el sistema de ficheros local del Manager, en la ruta:
`/var/opt/morpheus/bitcan/backup/backup.1`

![vme-backups-01]({{ site.imagesposts2026 }}/03/vme-backups-01.png){: .mx-auto.d-block :}

De forma nativa, existe un job llamado "Morpheus Appliance" que es el encargado de proteger toda la configuración del Manager. Este job se ejecuta de forma automática y genera el dump de MySQL.

![vme-backups-02]({{ site.imagesposts2026 }}/03/vme-backups-02.png){: .mx-auto.d-block :}

# Restauración de VME manager

El procedimiento de restore es relativamente sencillo. Básicamente consiste en restaurar el dump de la BBDD previamente creado y reiniciar los servicios. Vamos a ello…

1. Descomprimir el backup
El backup se descarga como un archivo ZIP. Lo descomprimimos:
unzip backup.1.20251030121307.zip
El fichero que nos interesa dentro del ZIP es el que se llama morpheus, que contiene el dump de la BBDD.

2. Parar el servicio de la UI
morpheus-ctl stop morpheus-ui

3. Obtener la contraseña de la BBDD
La contraseña del usuario de MySQL se puede obtener del fichero de configuración:
cat /etc/morpheus/morpheus-secrets.json | grep morpheus_password

4. Restaurar el dump
Con la contraseña en mano, ejecutamos el restore:
/opt/morpheus/embedded/mysql/bin/mysql -u morpheus -h 127.0.0.1 morpheus -p \
  < /var/opt/morpheus/bitcan/backup/backup.1/morpheus

5. Arrancar de nuevo los servicios
morpheus-ctl start morpheus-ui

Y ya tendríamos nuestro Manager completamente operativo y funcional.


![vme-backups-03]({{ site.imagesposts2026 }}/03/vme-backups-03.png){: .mx-auto.d-block :}

![vme-backups-04]({{ site.imagesposts2026 }}/03/vme-backups-04.png){: .mx-auto.d-block :}



https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007322en_us&page=GUID-1E710344-0932-4A51-B605-18AEF716E46F.html

Antes de empezar, es altamente recomendable revisar el upgrade path entre versiones. Esto lo podremos encontrar en la documentación oficial del producto, [aquí](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007027en_us&page=GUID-B7279DC1-CAB8-4172-8874-29A0FE86C772.html)

En mi caso, pretendo subir de la versión 8.0.10 a la 8.0.11

![updates-01]({{ site.imagesposts2026 }}/02/updates-01.png){: .mx-auto.d-block :}

Como comento, en mi laboratorio partiremos de la versión 8.0.10 que podremos validar en la parte inferior derecha.

![updates-02]({{ site.imagesposts2026 }}/02/updates-02.png){: .mx-auto.d-block :}

# Procedimiento actualización VME Manager

Iniciaremos el procedimiento subiendo el binario que previamente hemos descargado del portal de licencias de HPE a nuestro manager. Por ejemplo con WinSCP

![updates-03]({{ site.imagesposts2026 }}/02/updates-03.png){: .mx-auto.d-block :}

![updates-04]({{ site.imagesposts2026 }}/02/updates-04.png){: .mx-auto.d-block :}

Detendremos el servicio UI con el comando `sudo morpheus-ctl stop morpheus-ui`

![updates-05]({{ site.imagesposts2026 }}/02/updates-05.png){: .mx-auto.d-block :}

Lanzaremos la actualización con el comando `sudo dpkg -i HPE_VM_Essentials_vXXXXXXX....`

![updates-06]({{ site.imagesposts2026 }}/02/updates-06.png){: .mx-auto.d-block :}

Durante el procedimiento de actualización veremos de la versión que venimos y hacia a la que vamos y finalmente el proceso de actualización finalizará.

![updates-07]({{ site.imagesposts2026 }}/02/updates-07.png){: .mx-auto.d-block :}

Ya con el nuevo binario instalado, ejecutaremos la reconfiguración con el comando `sudo morpheus-ctl reconfigure`

![updates-08]({{ site.imagesposts2026 }}/02/updates-08.png){: .mx-auto.d-block :}

![updates-09]({{ site.imagesposts2026 }}/02/updates-09.png){: .mx-auto.d-block :}

Podremos validar que todos los servicios han arrancado de nuevo con el comando `sudo morpheus-ctl status`

![updates-10]({{ site.imagesposts2026 }}/02/updates-10.png){: .mx-auto.d-block :}

Y podremos volver a validar la versión final en la parte inferior derecha

![updates-11]({{ site.imagesposts2026 }}/02/updates-11.png){: .mx-auto.d-block :}

# Actualización agentes HVM

Tras la actualización del Manager, nos quedará actualizar los nodos HVM.

Desde el menú de Infrastructure > Compute > node veremos que aparece una notificación que nos recomienda actualizar.

Es tan fácil como iniciar la actualización de los agentes desde el botón de Actions > Upgrade Agent

![updates-12]({{ site.imagesposts2026 }}/02/updates-12.png){: .mx-auto.d-block :}

![updates-13]({{ site.imagesposts2026 }}/02/updates-13.png){: .mx-auto.d-block :}

Como podeis ver, el proceso es relativamente sencillo y tardaremos pocos minutos en actualizar nuestro entorno de HPE VM Essentials

Nos vemos en el próximo post ;-)

Un saludo

Miquel.