---
title: Creando un entorno JMP con VMware Horizon - Parte 15 - Instalación Dynamic Environment Manager
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
permalink: /jmp-part15/

---

https://univirt.wordpress.com/2018/02/20/building-a-horizon-view-jmp-lab-part-1-introduction/

https://www.sistel.es/gestion-del-entorno-del-usuario-horizon-7-uem

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

# Descargar última versión e instalación plantillas ADMX

A fecha de edición de este post, la última versión disponible es la  9.11, así que nos descargaremos esa versión
![dem_download]({{ site.imagesposts2019 }}/08/dem_download01.png){: .align-center}

En el fichero que nos descargemos, encontraremos una carpeta con unas plantillas .admx y sus correspondientes ficheros de idioma. Tendremos que copiarlos en nuestro DC para poder crear posteriormente las GPO

![uem_config1]({{ site.imagesposts2019 }}/08/uem_config1.png){: .align-center}

# Crear carpetas compartidas y configuración permisos

De entrada, necesitaremos 3 carpetas compartidas

* DEM_CONFIG > Se almacenará la configuración general de DEM
* DEM_PROFILES > Dónde cada usuario almacenará la información relacionada con su perfil
* DEM_FOLDERREDIRECTION > Dónde configuraremos la redirección de carpetas cómo el Escritorio, Mis Docuentos, Favoritos, etc etc.

A nivel de share, daremos control total a todos los usuarios, ya que controlaremos los accesos a nivel de NTFS

![dem_permisos01]({{ site.imagesposts2019 }}/08/dem_permisos01.png){: .align-center}

## DEM_CONFIG

*Administradores:* Control total
*Usuarios:* Lectura

![dem_permisos02]({{ site.imagesposts2019 }}/08/dem_permisos02.png){: .align-center}

## DEM_PROFILE

*Administradores:* Control total
*Usuarios:* Lectura/ejecución (sólo en esta carpeta)
*Propietario:* Control total

![dem_permisos03]({{ site.imagesposts2019 }}/08/dem_permisos03.png){: .align-center}

## DEM_FOLDERREDIRECTION

*Administradores:* Control total
*Usuarios:* Lectura/ejecución (sólo en esta carpeta)
*Propietario:* Control total

![dem_permisos04]({{ site.imagesposts2019 }}/08/dem_permisos04.png){: .align-center}

## DEM_LOGS

*Administradores:* Control total
*Usuarios:* Lectura/ejecución (sólo en esta carpeta)
*Propietario:* Control total

![dem_permisos05]({{ site.imagesposts2019 }}/08/dem_permisos05.png){: .align-center}

# Instalación DEM Management Console

![dem_instalation01]({{ site.imagesposts2019 }}/08/dem_instalation01.png){: .align-center}
![dem_instalation02]({{ site.imagesposts2019 }}/08/dem_instalation02png){: .align-center}
![dem_instalation03]({{ site.imagesposts2019 }}/08/dem_instalation03.png){: .align-center}
![dem_instalation04]({{ site.imagesposts2019 }}/08/dem_instalation04.png){: .align-center}
![dem_instalation05]({{ site.imagesposts2019 }}/08/dem_instalation05.png){: .align-center}
![dem_instalation06]({{ site.imagesposts2019 }}/08/dem_instalation06.png){: .align-center}
![dem_instalation07]({{ site.imagesposts2019 }}/08/dem_instalation07.png){: .align-center}
![dem_instalation08]({{ site.imagesposts2019 }}/08/dem_instalation08.png){: .align-center}

# Configuración GPO

![dem_gpo01]({{ site.imagesposts2019 }}/08/dem_gpo01.png){: .align-center}
![dem_gpo02]({{ site.imagesposts2019 }}/08/dem_gpo02.png){: .align-center}

![dem_gpo03]({{ site.imagesposts2019 }}/08/dem_gpo03.png){: .align-center}
![dem_gpo04]({{ site.imagesposts2019 }}/08/dem_gpo04.png){: .align-center}
![dem_gpo05]({{ site.imagesposts2019 }}/08/dem_gpo05.png){: .align-center}
![dem_gpo06]({{ site.imagesposts2019 }}/08/dem_gpo06.png){: .align-center}
![dem_gpo07]({{ site.imagesposts2019 }}/08/dem_gpo07.png){: .align-center}
![dem_gpo08]({{ site.imagesposts2019 }}/08/dem_gpo08.png){: .align-center}
![dem_gpo09]({{ site.imagesposts2019 }}/08/dem_gpo09.png){: .align-center}
![dem_gpo10]({{ site.imagesposts2019 }}/08/dem_gpo10.png){: .align-center}
![dem_gpo11]({{ site.imagesposts2019 }}/08/dem_gpo11.png){: .align-center}

# Instalación DEM agent



Espero que os sirva.

Un saludo!

Miquel.


