---
title: Consideraciones sobre el disco de arranque en ESXi 7.x
date: '2021-11-18 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- vexpert
- esxi

---

En las últimas semanas, han sido varios los usuarios que han reportado en diferentes foros y RRSS errores con las SD y/o USB de arranque al actualizar a vSphere 7.0

En este post vamos a repasar que dice VMware en su guía técnica y las recomendaciones que hace al respecto para poder mitigarlo.

Los disipositivos USB o tarjetas SD han sido utilizadas historicamente para instalar nuestro ESXi y así poder prescindir de discos/controladora en nuestros servidores.
El problema de estos dispositivos es que tienen menos resistencia que un disco tradicional y ademas pueden presentar problemas de rendimiento a la hora de exigirles una alta frecuéncia de IOPS. Ahora, con ESXi 7.x estamos siendo testigos de estos problemas con el arranque con mayor frecuencia que en versiones anteriores.

Antes de profundizar en detalles, es importante comprender el nuevo diseño del sistema de arranque en ESXi 7.x. En versiones anteriores, los tamaños de particiones eran fijos y el número de partición estático. Eso provocaba algunas limitaciones en el uso de otras soluciones cómo NSX-T, vSAN, Tanzu, etc etc lo que restringía la compatibilidad con la instalación de módulos grandes por ejemplo.

De cara a esta necesidad para que los ESXi sean compatibles con otras soluciones de VMware o de terceros es necesario disponer de dispositivos mas robustos, flexibles y de alto rendimiento.

Con la nueva arquitectura de particiones en vSphere 7.0, sólo la partición de arranque del sistema es de tamaño fijo. El resto de particiones son dinámicas, por lo que el tamaño se determinará en función del tamaño del dispositivo de arranque.


![boot-media-1]({{ site.imagesposts2021 }}/11/boot-media-1.png){: .align-center}






https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-28156B0F-09AD-4B44-BC29-BFA91773DD46.html#GUID-28156B0F-09AD-4B44-BC29-BFA91773DD46__FIG_A94B7B89-5EC6-4C26-8730-534A15EEDCE1

https://virtualtassie.com/2018/vcenter-6-7-cross-sso-domain-repointing/


cmsso-util domain-repoint -m pre-check --src-emb-admin Administrator --replication-partner-fqdn vcenter-p.miquelmariano.github.io --replication-partner-admin administrator --dest-domain-name vsphere.local

cmsso-util domain-repoint -m execute --src-emb-admin administrator@vsphere.local --replication-partner-fqdn vcenter-p.miquelmariano.github.io --replication-partner-admin administrator@vsphere.local --dest-domain-name vsphere.local

cmsso-util domain-repoint -m execute --src-emb-admin Administrator  --dest-domain-name vsphere.local


![writable_volumes000]({{ site.imagesposts2020 }}/04/writable_volumes000.png){: .align-center}



Espero que os guste.

Un saludo!

Miquel.


