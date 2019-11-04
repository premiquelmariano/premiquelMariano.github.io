---
title: Instalar parches en ESXi sin Update Manager
date: '2019-11-01 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- vexpert
- update
- esxi

---

Ansibilizar también el proceso

https://www.techcrumble.net/2019/05/how-to-update-esxi-without-update-manager/

https://my.vmware.com/group/vmware/patch#search



# Descargar paquete

![uppdate-esxi-without-um-01]({{ site.imagesposts2019 }}/11/update-esxi-without-um-01.png){: .align-center}

![uppdate-esxi-without-um-02]({{ site.imagesposts2019 }}/11/update-esxi-without-um-02.png){: .align-center}

![uppdate-esxi-without-um-03]({{ site.imagesposts2019 }}/11/update-esxi-without-um-03.png){: .align-center}

```ssh
esxcli software vib install -d /vmfs/volumes/LOCAL/update-from-esxi6.7-6.7_update03.zip
```

Espero que os sirva.

Un saludo!

Miquel.


