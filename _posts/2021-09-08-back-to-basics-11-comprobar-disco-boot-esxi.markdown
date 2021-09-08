---
title: Back-to-basics 11 - Comprobar el disco de arranque o boot en nuestros servidores ESXi
date: '2021-09-08 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- esxi
- vsphere
- vexpert
---

En el dia de hoy os traigo un pequeño manual para comprobar cual es el disco de arranque de nuestros servidores ESXi. 

Este post, forma parte de la serie [back to basics](https://miquelmariano.github.io/tag/#/backtobasics), que hacia tiempo que no actualizaba ;-)

# 1. Habilitamos el servicio SSH en nuestro servidor ESXi

# 2. Hacemos login a nuestro SSH utilizando un usuario con privilegios de root

# 3. Ejecutamos el siguiente comando para ver el volumen de arranque

```
#ls -l /bootbank | awk -F"-> " '{print $2}'
```

Deberiamos tener una salida similar a esta:

```
[root@esxi01:~] ls -l /bootbank | awk -F"-> " '{print $2}'
/vmfs/volumes/50705ae3-b08ce25f-a1b8-bc56258253ad
```

# 4. Copy vmfs volume and run below command to get more details about volume. 

```
#vmkfstools -P vmfsVolumeID
```

```
[root@esxi01:~] vmkfstools -P /vmfs/volumes/50705ae3-b08ce25f-a1b8-bc56258253ad
vfat-0.04 (Raw Major Version: 0) file system spanning 1 partitions.
File system label (if any):
Mode: private
Capacity 261853184 (63929 file blocks * 4096), 90677248 (22138 blocks) avail, max supported file size 0
UUID: 50705ae3-b08ce25f-a1b8-bc56258253ad
Partitions spanned (on "disks"):
        eui.00a0504658335330:5
Is Native Snapshot Capable: NO
```

# 5. From above command output copy the disks/partition UID and run below command to get device details. 

```
#esxcli storage core device list | grep -A27 deviceID
```

```
[root@esxi01:~] esxcli storage core device list | grep -A27 eui.00a0504658335330
eui.00a0504658335330
   Display Name: Local USB Direct-Access (eui.00a0504658335330)
   Has Settable Display Name: false
   Size: 30436
   Device Type: Direct-Access
   Multipath Plugin: NMP
   Devfs Path: /vmfs/devices/disks/eui.00a0504658335330
   Vendor: Cypress
   Model: SDRAID
   Revision: 0000
   SCSI Level: 2
   Is Pseudo: false
   Status: on
   Is RDM Capable: false
   Is Local: true
   Is Removable: true
   Is SSD: false
   Is VVOL PE: false
   Is Offline: false
   Is Perennially Reserved: false
   Queue Full Sample Size: 0
   Queue Full Threshold: 0
   Thin Provisioning Status: unknown
   Attached Filters:
   VAAI Status: unsupported
   Other UIDs: vml.0000000000766d68626133323a303a30
   Is Shared Clusterwide: false
   Is Local SAS Device: false
   Is SAS: false
   Is USB: true
   Is Boot USB Device: true
   Is Boot Device: true
   Device Max Queue Depth: 1
   No of outstanding IOs with competing worlds: 32
```

In above command you can see, this ESXi host is booted and running from USB device. 

Above process looks simple and useful. 
If you have large number of ESXi hosts and want to export all ESXi hosts boot device then you can automate it using PowerShell and bash scripting. 





Espero que os guste ;-)

Saludos!

Miquel.


