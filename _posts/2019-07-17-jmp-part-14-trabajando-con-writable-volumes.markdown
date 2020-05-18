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

Sacado de la documentación oficial, los Writable Volumes, son volúmenes dónde los usuarios pueden guardar sus propios datos y configuraciones específicos de su perfil. Este volumen se asigna a cada usuario y los datos que ahí se almacenan se migran con el usuario en las diferentes máquinas donde se inicie sesión.

Sería un sistema parecido a los tradicionales Persistent Disk que se usan en los escritorios Linked Clone. La principal ventaja de un Writable Volume frente a un Persistent Disk es que el Writable va siempre con el usuario, mientras que un Persistent Disk, a parte de estar atado a un usuario, también lo está a un escritorio.

Con persistent disk, si un usuario tiene varios escritorios Linked Clone deberá tener múltiples Persistent Disk uno por escriorio. Con Writable Volumes, el usuario podrá iniciar sesión en múltiples escritorios (no de forma simultánea) y sus datos se vincularán automáticamente a cada escritorio.

#	¿Para qué se usan los Writable Volumes?

Los writable volumes básicamente están diseñados para garantizar y dar continuidad a los datos de usuario en entornos no-persistentes. Configuraciones de aplicación, perfil de usuario, información de licencia, ficheros de configuración o incluso aplicaciones instaladas por el propio usuario son algunos ejemplos de lo que se guardará en este volúmen.

![writable_volumes001]({{ site.imagesposts2020 }}/04/writable_volumes001.png){: .align-center}

#	Diferentes plantillas de Writable Volumes

Una plantilla, en Writable Volumes, es un disco .vmdk en dónde se especifica qué datos de usuario se guardarán. A partir de esta plantilla, se crearán los Writable Volumes de cada usuario y dependiendo de ella, se guardará una u otra información.

Por defecto, en cualquier instalación de App Volumes están disponibles 3 plantillas:

- template_profile_only.vmdk (10Gb)
- template_uia_only.vmdk (10Gb)
- template_uia_plus_profile.vmdk (10Gb)

**User Profile Data Only:** Guarda únicamente datos del perfil de usuario.

**User Installed Applications Only:** Guarda únicamente aplicaciones que el usuario se pueda instalar en su escritorio.

**Both Profile Data and User Installed Applications:** Guarda las 2 cosas, el perfil del usuario y las aplicaciones.

Por defecto, estos perfiles tienen una capacidad de 10Gb., más adelante veremos cómo modificarlos y crear nuestros propios perfiles.

#	Creación de Writable Volumes

El proceso de creación de un Writable Volume es tremendamente sencillo y consta de las siguientes fases:

![writable_volumes000]({{ site.imagesposts2020 }}/04/writable_volumes000.png){: .align-center}

En la pestaña Writables > Create
![writable_volumes002]({{ site.imagesposts2020 }}/04/writable_volumes002.png){: .align-center}

Buscaremos al usuario o grupo de usuarios al que queramos asociar ese Writable Volume así cómo el datastore donde se almacenará y la plantilla en la que nos basaremos.
![writable_volumes003]({{ site.imagesposts2020 }}/04/writable_volumes003.png){: .align-center}

Creamos el volúmen en background
![writable_volumes004]({{ site.imagesposts2020 }}/04/writable_volumes004.png){: .align-center}

Y ya tendremos el volúmen. De momento en estado "Detached"
![writable_volumes005]({{ site.imagesposts2020 }}/04/writable_volumes005.png){: .align-center}

Al iniciar sesión en nuestro VDI con el App Volumes Agent instalado, automáticamente se nos vinculará otro disco correspondiente a nuestro Writable Volume
![writable_volumes006]({{ site.imagesposts2020 }}/04/writable_volumes006.png){: .align-center}

Y desde el App Volumes Manager, veremos que el estado a pasado a "Attached"
![writable_volumes007]({{ site.imagesposts2020 }}/04/writable_volumes007.png){: .align-center}

#	¿Cómo editar un template de Writable Volumes?

https://ageroskam.nl/app-volumes-2-x/manage-user-profiles-with-writable-volumes/

Toda la configuración de un writable volume está en un fichero llamado **snapvol.cfg**. Este fichero está en la carpeta raíz de cualquier writable volume, también en los templates.

El fichero contiene la información referente a qué debe ser capturado y qué no en ese writable volume. Este fichero de configuración no solo contiene los path de las carpetas que se tienen que guardar o excluir, sinó que también incluye ramas del registro que se deben capturar.

En definitiva, con esta fichero podremos customizar a medida el comportamiento que tendrán nuestros writable volumes en función de nuestras necesidades.

## ¿Cómo editar el fichero snapvol.cfg?

Para poder customizar a nuestro gusto un template, lo que os recomiendo es hacer un clon de uno existente que nos sirva de base.

Seleccionaremos la plantilla y Copiar en:
![writable_volumes008]({{ site.imagesposts2020 }}/04/writable_volumes008.png){: .align-center}

Generaremos una cópia en la carpeta cloudvolumes ya que no puede haber 2 ficheros con el mismo nombre en una carpeta:
![writable_volumes008]({{ site.imagesposts2020 }}/04/writable_volumes008.png){: .align-center}

Le cambiaremos el nombre y posteriormente lo volveremos a dejar en la carpeta writable_templates:
![writable_volumes009]({{ site.imagesposts2020 }}/04/writable_volumes009.png){: .align-center}

![writable_volumes010]({{ site.imagesposts2020 }}/04/writable_volumes010.png){: .align-center}

![writable_volumes011]({{ site.imagesposts2020 }}/04/writable_volumes011.png){: .align-center}

![writable_volumes012]({{ site.imagesposts2020 }}/04/writable_volumes012.png){: .align-center}

Un saludo!

Miquel.


