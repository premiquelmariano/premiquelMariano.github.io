---
title: FSLogix
date: '2021-04-22 00:00:00'
layout: post
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
- fslogix
---

# Que es FSLogix?

Cogiendo la definición oficial de la [documentación de Microsoft](https://docs.microsoft.com/en-us/fslogix/overview)

"FSLogix is a set of solutions that enhance, enable, and simplify non-persistent Windows computing environments. FSLogix solutions are appropriate for Virtual environments in both public and private clouds. FSLogix solutions may also be used to create more portable computing sessions when using physical devices."

Dicho de otra manera. FSLogix, es una solución de gestión de perfiles de usuarios que almacena todos los datos del usuario en un disco VDH montado independientemente. Para los que son del mundo Horizon, seria (salvando las distancias) como el persistent disk que teniamos antaño con los Linked Clone

# Cómo encaja FSLogix en el resto de productos del stack Horizon?

Me he encontrado por ahi este maravilloso diagrama que me parece que explica a la perfección en que lugar queda FSLogix

![fslogix-schema]({{ site.imagesposts2021 }}/04/fslogix-schema.png){: .align-center}

Básicamente, con FSLogix capturaremos los datos de usuario (Escritorio, Mis Documentos, Descargas, etc etc...) y también la configuración, el AppData del usuario.

Luego está DEM que gestiona las configuraciones pre-definidas y el propio entorno del usuario, aunque también pueda capturar la configuración (AppData)

Por último, aunque APP Volumes también permite "Writtable Volumes", nació cómo una funcionalidad nativa de virtualización de aplicaciones.


![fslogix-00]({{ site.imagesposts2021 }}/04/fslogix-00.png){: .align-center}
![fslogix-01]({{ site.imagesposts2021 }}/04/fslogix-01.png){: .align-center}
![fslogix-02]({{ site.imagesposts2021 }}/04/fslogix-02.png){: .align-center}
![fslogix-03]({{ site.imagesposts2021 }}/04/fslogix-03.png){: .align-center}
![fslogix-04]({{ site.imagesposts2021 }}/04/fslogix-04.png){: .align-center}
![fslogix-05]({{ site.imagesposts2021 }}/04/fslogix-05.png){: .align-center}
![fslogix-06]({{ site.imagesposts2021 }}/04/fslogix-06.png){: .align-center}
![fslogix-07]({{ site.imagesposts2021 }}/04/fslogix-07.png){: .align-center}
![fslogix-08]({{ site.imagesposts2021 }}/04/fslogix-08.png){: .align-center}
![fslogix-09]({{ site.imagesposts2021 }}/04/fslogix-09.png){: .align-center}
![fslogix-10]({{ site.imagesposts2021 }}/04/fslogix-10.png){: .align-center}
![fslogix-11]({{ site.imagesposts2021 }}/04/fslogix-11.png){: .align-center}
![fslogix-12]({{ site.imagesposts2021 }}/04/fslogix-12.png){: .align-center}
![fslogix-13]({{ site.imagesposts2021 }}/04/fslogix-13.png){: .align-center}

https://minarik.io/fslogix-and-horizon-quick-and-dirty-setup/
https://docs.microsoft.com/es-es/azure/virtual-desktop/fslogix-containers-azure-files