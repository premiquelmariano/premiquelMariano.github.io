---
title: Migrar vcenter a otro SSO con ELM
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

---

https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-28156B0F-09AD-4B44-BC29-BFA91773DD46.html#GUID-28156B0F-09AD-4B44-BC29-BFA91773DD46__FIG_A94B7B89-5EC6-4C26-8730-534A15EEDCE1

https://virtualtassie.com/2018/vcenter-6-7-cross-sso-domain-repointing/


cmsso-util domain-repoint -m pre-check --src-emb-admin Administrator --replication-partner-fqdn vcenter-p.miquelmariano.github.io --replication-partner-admin administrator --dest-domain-name vsphere.local

cmsso-util domain-repoint -m execute --src-emb-admin administrator@vsphere.local --replication-partner-fqdn vcenter-p.miquelmariano.github.io --replication-partner-admin administrator@vsphere.local --dest-domain-name vsphere.local

cmsso-util domain-repoint -m execute --src-emb-admin Administrator  --dest-domain-name vsphere.local


![writable_volumes000]({{ site.imagesposts2020 }}/04/writable_volumes000.png){: .align-center}



Espero que os guste.

Un saludo!

Miquel.


