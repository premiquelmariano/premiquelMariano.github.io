---
title: Cómo instalar y configurar VMware PowerCLI 11.1
date: '2017-09-22 00:00:00'
layout: post
image: /assets/images/posts/2019/01/PowerShell6-banner.jpg
headerImage: true
tag:
- automation
- ansible
- devops
category: blog
author: miquelMariano
description: Cómo instalar y configurar VMware PowerCLI 10
hidden: false
permalink: /powercli10/
---

https://thesolving.com/es/virtualizacion/como-instalar-y-configurar-vmware-powercli-version-10/
http://thesolving.com/virtualization/how-to-install-and-configure-vmware-powercli-version-10/
https://ithinkvirtual.com/2018/03/04/install-powershell-and-vmware-powercli-on-macos/

Buenos dias a tod@as!!
En el post de hoy veremos cómo instalar la última versión de PowerCLI 11.1 sobre windows

Como sabeis, VMware PowerCLI es un conjunto de módulos de Powershell que se utilizan para gestionar, administrar,mantener y monitorizar un entorno VMware. 
Los que ya esteis familizarizados, habreis descubierto que es una poderosa herramienta para cualquier administrador de sistemas y puede utilizarse para recopilar información detallada y/o ejecutar comandos en múltiples máquinas virtuales, hosts etc, etc...

Tradicionalmente, PowerCLI se instalaba sobre un sistema Windows y VMWare nos proporcionaba un instalador .msi en el que sólo habia que seguir el tradicional wizard siguiente>siguiente>fin.

Desde la versión 6.5.1, eso cambió, y PowerCLI se instala directamente desde PowerShell. Eso abre un amplio abanico de posibilidades ya que también desde la llegada de PowerShell 6.0 Core, se puede instalar sobre Linux e incluso sobre MAC, pero bueno, eso lo veremos en otro post.

Para instralar PowerCLI 11.1 (última version disponible a fecha de hoy) hay que tener PowerShell 3.0 o superior. A continuación vamos a ver como instalar la última versión de PowerShell para windows.

### 1) Descargamos la última versión para nuestro SO desde el repositorio oficial.

Descargar PowerShell Core desde aquí
https://github.com/PowerShell/PowerShell

![ps6-0]({{ site.imagesposts2019 }}/01/PowerShell6-0.png)

![ps6-1]({{ site.imagesposts2019 }}/01/PowerShell6-1.png)

![ps6-2]({{ site.imagesposts2019 }}/01/PowerShell6-2.png)

![ps6-3]({{ site.imagesposts2019 }}/01/PowerShell6-3.png)

![ps6-4]({{ site.imagesposts2019 }}/01/PowerShell6-4.png)

![ps6-5]({{ site.imagesposts2019 }}/01/PowerShell6-5.png)

![ps6-6]({{ site.imagesposts2019 }}/01/PowerShell6-6.png)

![ps6-7]({{ site.imagesposts2019 }}/01/PowerShell6-7.png)

![ps6-8]({{ site.imagesposts2019 }}/01/PowerShell6-8.png)

```powershell
Save-Module -Name VMware.PowerCLI -Path <path>
```

![ps6-9]({{ site.imagesposts2019 }}/01/PowerShell6-9.png)

```powershell
Install-Module -Name VMware.PowerCLI
```

![ps6-10]({{ site.imagesposts2019 }}/01/PowerShell6-10.png)

![ps6-11]({{ site.imagesposts2019 }}/01/PowerShell6-11.png)

```powershell
Get-Module -ListAvailable -Name VMware*
```

![ps6-12]({{ site.imagesposts2019 }}/01/PowerShell6-12.png)

```powershell
Set-PowerCLIConfiguration -InvalidCertificateAction:Ignore
```

![ps6-13]({{ site.imagesposts2019 }}/01/PowerShell6-13.png)






Un saludo!

Miquel.


