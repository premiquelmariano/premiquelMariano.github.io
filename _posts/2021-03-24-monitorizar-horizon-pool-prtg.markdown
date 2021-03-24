---
title: Script para monitorizar estadísticas de uso en un pool Horizon
date: '2021-03-24 00:00:00'
layout: post
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
- centos8
- powershell
- powercli
---

Hoy quiero compartir con todos vosotros un script en PowerCLI que he escrito para monitorizar las estadísticas de nuestros pooles de VMware Horizon e integrarlo con PRTG

# VMware PowerCLI para horizon

Hace ya tiempo, compartí un procedimiento de [cómo instalar y configurar VMware PowerCLI](https://miquelmariano.github.io/2019/01/09/instalar-powerCLI-10-windows/). A dia de hoy ya vamos por la versión 7 de powershell y la versión 12 de PowerCLI, pero el procedimiento sigue siendo válido.

Una vez tengamos PowerShell instalado y los módulos también instalados, podremos comprobar que ya está disponible

```powershell
get-module -listavailable
```
![powercli-horizon-01]({{ site.imagesposts2021 }}/03/powercli-horizon-01.png){: .align-center}

