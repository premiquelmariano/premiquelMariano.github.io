---
title: Comandos útiles virsh
subtitle: Parte 10 - Lista de comandos mas útiles para gestionar VM Essentials
date: '2026-10-19 00:00:00'
layout: post
thumbnail-img: https://miquelmariano.github.io/assets/images/posts/2025/10/hpe_morpheus_01.jpg
cover-img: https://miquelmariano.github.io/assets/images/fondos/10.jpg
share-img: https://miquelmariano.github.io/assets/images/posts/2025/10/hpe_morpheus_01.jpg
published: true
author: Miquel Mariano
tag:
- kvm
- hpe
- vme
- cloud
- morpheus
- ha
- veeam
---

HPE VM Essentials (Morpheus) corre sobre KVM/libvirt, así que cada nodo del clúster se puede gobernar con `virsh`. La consola de gestión (el manager) cubre el 90 % del día a día, pero cuando algo se tuerce (una VM que no arranca, un checkpoint huérfano de Veeam, una migración desde vSphere que te deja sin red) `virsh` es la herramienta que te saca del apuro. 

Este post porma parte de la serie sobre HPE VM Essentials y a continuación podeis ver el índice de toda la serie:

<details>
<summary>VER TODA LA SERIE DE POSTS SOBRE VME</summary>

<ul>
  <li><a href="https://miquelmariano.github.io/introduccion-hpe-morpheus-vm-essentials-software/">Parte 1 - Introducción a HPE Morpheus VM Essentials software</a></li>
  <li><a href="https://miquelmariano.github.io/instalacion-nodo-vme/">Parte 2 - Instalación VM Essentials software</a></li>
  <li><a href="https://miquelmariano.github.io/instalacion-manager/">Parte 3 - Instalación VME Manager</a></li>
  <li><a href="https://miquelmariano.github.io/configuracion-inicial-primeros-pasos-vm-essentials">Parte 4 - Configuración inicial</a></li>
  <li><a href="https://miquelmariano.github.io/cluster-ceph/">Parte 5 - Creación cluster Ceph</a></li>
  <li><a href="https://miquelmariano.github.io/primera-vm-en-vmessentials/">Parte 6 - Desplegar nuestra primera VM</a></li>
  <ul>
      <li><a href="https://miquelmariano.github.io/ampliar-disco-vm-windows-sobre-vme/">Parte 6.1 - Ampliar disco en servidor Windows</a></li>
    </ul>
  <li><a href="https://miquelmariano.github.io/backups-en-vm-essentials/">Parte 7 - Backups nativos</a>
  <ul>
      <li><a href="https://miquelmariano.github.io/backup-vme-con-veeam/">Parte 7.1 - Backups con Veeam v13</a></li>
  </ul>  
  </li>
  <li><a href="https://miquelmariano.github.io/ha-en-vm-essentials/">Parte 8 - Pruebas de HA</a></li>
  <li><a href="https://miquelmariano.github.io/migracion-vsphere-vme/">Parte 9 - Migración de VMs desde vSphere</a>
    <ul>
      <li><a href="https://miquelmariano.github.io/migracion-vsphere-vme-veeam/">Parte 9.1 - Migración con Veeam</a></li>
    </ul>
  </li>
  <li>[Parte 10 - Comandos útiles]</li>
  <li><a href="https://miquelmariano.github.io/actualizaciones-vme-manager-y-nodos-hvm">Parte 11 - Gestión de actualizaciones en HPE VM Essentials</a></li>
</ul>

</details>

{: .box-note}
- Todos los comandos se lanzan en el nodo donde corre la VM, con sudo.
- Lo que cambies con virsh no pasa por el manager de VME. Para tareas rutinarias (cambiar CPU, RAM, discos o NICs) usa la consola de VME. Reserva virsh para diagnóstico y para los casos en que el manager no llega.
- Los ejemplos son de mi laboratorio. Sustituye nombres, IDs, IPs y credenciales por los tuyos.

# Listar y monitorizar VMs

`virsh list`
Lista las VMs en ejecución. Con `--all` incluye también las apagadas.

```ssh
 Id   Name             State
----------------------------------
 1    vme-manager-01   running
 7    encora-01        running
 134  FS-restored      running
 -    veeam-worker-01  shut off
 ````

El `Id` es el identificador de dominio que luego puedes usar en lugar del nombre en cualquier comando. Ojo: cambia cada vez que la VM se apaga y se vuelve a encender.

`virsh dominfo`
Estado actual (running, paused, shut off...).

```ssh
sudo virsh domstate FS-restored
```

`virsh domstats`
Estadísticas de CPU, memoria, disco y red.

```ssh
sudo virsh domstats FS-restored
```

# Controlar el estado de una VM

| Comando | Qué hace |
| :--- | :--- |
| `virsh start VM` | Arranca una VM apagada |
| `virsh shutdown VM` | Apagado ordenado (necesita ACPI o guest agent en el guest) |
| `virsh destroy VM` | Apagado forzoso, como tirar del cable. Úsalo con cuidado |
| `virsh reboot VM` | Reinicio ordenado |
| `virsh suspend VM` | Pausa la VM en memoria |
| `virsh resume VM` | Reanuda una VM pausada |

Si `shutdown` no hace nada, el guest no está procesando ACPI. Es habitual en Windows con el agente sin instalar o con la VM bloqueada en la pantalla de login.

# Editar la configuración de una VM

`virsh edit`
Abre el XML de la VM en tu editor. Edítala con la VM apagada y ten presente que el manager puede sobrescribir cambios manuales.

```ssh
sudo virsh edit FS-restored
```

`virsh setvcpus`
Cambia el número de vCPUs. Con la VM apagada, añade --config para que persista.

```ssh
sudo virsh setvcpus FS-restored 4 --config
```

`virsh setmem`
Cambia la memoria asignada. Por defecto el valor va en KiB y no puede superar el máximo definido para la VM.

```ssh
sudo virsh setmem FS-restored 8388608 --config
```

8388608 KiB son 8 GiB.

# Almacenamiento y red

`virsh attach-disk`
Añade un disco o una ISO a una VM.

```ssh
virsh attach-disk FS-restored /ruta/disco.qcow2 vdb --persistent
virsh attach-disk FS-restored /ruta/virtio-win.iso sdz --type cdrom --mode readonly
```

`virsh detach-disk`
Quita un disco por su target.

```ssh
sudo virsh detach-disk FS-restored vdb --persistent
```

`virsh attach-interface`
Añade una interfaz de red.

```ssh
sudo virsh attach-interface FS-restored network default --model virtio --persistent
```

`virsh detach-interface`
Quita una interfaz. Necesita el tipo y, si hay varias, la MAC.

```ssh
sudo virsh detach-interface FS-restored network --mac 52:54:00:aa:bb:cc --persistent
```

La MAC la ves con virsh domiflist FS-restored.

# Comandos adicionales

`virsh autostart`
Controla si la VM arranca con el host.

```ssh
sudo virsh autostart FS-restored
sudo virsh autostart --disable FS-restored
```

# Eliminar una VM sin dejar rastro

Primero se para y luego se elimina la definición junto con todo lo asociado.

```ssh
sudo virsh list --all
sudo virsh destroy 2
sudo virsh undefine hpe-vme-manager --remove-all-storage --wipe-storage --snapshots-metadata --managed-save
```

Salida:

```ssh
Domain 'hpe-vme-manager' has been undefined
Wiping volume 'vda'(/var/morpheus/kvm/local/hpe-vm-essentials-8.1.2-1.qcow2) ... Done.
Volume 'vda'(/var/morpheus/kvm/local/hpe-vm-essentials-8.1.2-1.qcow2) removed.
```

Qué hace cada opción:
- `--remove-all-storage`: busca todos los discos asociados a la VM y los elimina.
- `--wipe-storage`: sobrescribe los datos del disco antes de borrar el fichero, para evitar su recuperación.
- `--snapshots-metadata`: borra cualquier registro de snapshots.
- `--managed-save`: elimina el estado guardado si la VM se había pausado alguna vez.

Es irreversible. Comprueba dos veces el nombre antes de lanzarlo.

# Ver en qué host está corriendo una VM

En un clúster de varios nodos, virsh solo ve lo que corre en el nodo local. Yo uso un pequeño script (`allssh.sh`) que ejecuta un comando en todos los nodos por SSH y lo agrupa por host:

``ssh
allssh.sh "sudo virsh list --all"
================== 10.10.10.101 =================
 Id   Name              State
----------------------------------
 13   ges-WinSrv2019    running
 28   mmr-test-03       running
 -    veeam-worker-01   shut off
================== 10.10.10.102 =================
 3    mmr-checkmk-01    running
 4    Win2025STD        running
```

Si no tienes un script así, un bucle sencillo hace lo mismo: `for h in 10.10.10.101 10.10.10.102 10.10.10.103; do ssh vmeadmin@$h "sudo virsh list --all"; done`.



En este ejemplo partimos de una VM con un disco de 30Gb en el que para ampliarlo seleccionaremos el botón de "Reconfigure" desde el menú "Actions"

![ampliar-disco-windows-01]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-01.png){: .mx-auto.d-block :}

Añadiremos el nuevo tamaño sin modificar ningún otro parámetro

![ampliar-disco-windows-02]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-02.png){: .mx-auto.d-block :}

En la pestaña "history" podremos comprobar que la tarea se ha realizado correctamente

![ampliar-disco-windows-03]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-03.png){: .mx-auto.d-block :}

# Ampliar unidad C

Con el disco ampliado podemos validar que nuestro windows ha detectado correctamente los +2GB adicionales que le hemos asignado.

Tambien vemos que entre la unidad C y el nuevo espacio se ha quedado la partición de recuperación de windows

![ampliar-disco-windows-04]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-04.png){: .mx-auto.d-block :}

La partición de recuperación de windows no se puede desplazar nativamente con la herramienta de diskpart por lo que en la mayoria de casos podemos optar por eliminarla.

- Abre el menú Inicio, busca **cmd** o **Símbolo del sistema**, haz clic derecho sobre él y selecciona Ejecutar como administrador.
- Abre la herramienta de gestión de discos: `diskpart`
- Lista los discos conectados a tu equipo: `list disk`
- Selecciona el disco principal donde está instalado Windows (reemplaza X por el número de tu disco, generalmente 0): `select disk X`
- Muestra la lista de particiones dentro de ese disco: `list partition`
- Identifica la partición de recuperación (suele indicarse como Recuperación o Recovery en la columna Tipo) y selecciónala (reemplaza Y por el número correspondiente): `select partition Y`
- Fuerza la eliminación de la partición de recuperación: `delete partition override`
- Sal de Diskpart: `exit`

![ampliar-disco-windows-05]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-05.png){: .mx-auto.d-block :}

Una vez eliminada la partición de recuperación y teniendo el espacio libre contiguo a C: podremos proceder a la ampliación de la unidad

![ampliar-disco-windows-06]({{ site.imagesposts2026 }}/09/ampliar-disco-windows-06.png){: .mx-auto.d-block :}

Nos vemos en el próximo post ;-)

Un saludo

Miquel.
