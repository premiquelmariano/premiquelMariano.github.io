---
title: Cómo instalar y configurar VMware PowerCLI 10
date: '2017-09-22 00:00:00'
layout: post
image: /assets/images/posts/2018/12/powercli10.png
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

Buenos dias a tod@as!!


https://thesolving.com/es/virtualizacion/como-instalar-y-configurar-vmware-powercli-version-10/
http://thesolving.com/virtualization/how-to-install-and-configure-vmware-powercli-version-10/
https://ithinkvirtual.com/2018/03/04/install-powershell-and-vmware-powercli-on-macos/


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






Un saludo!

Miquel.


