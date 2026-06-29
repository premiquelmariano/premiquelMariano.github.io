---
title: Backup de VMs en HPE VM Essentials con Veeam v13
subtitle: Parte 7.1 - Veeam Plug-in for HPE Morpheus VM Essentials
date: '2026-06-29 00:00:00'
layout: post
thumbnail-img: https://miquelmariano.github.io/assets/images/posts/2026/06/veeams13-vme-00.jpg
cover-img: https://miquelmariano.github.io/assets/images/fondos/09.jpg
share-img: https://miquelmariano.github.io/assets/images/posts/2026/06/veeams13-vme-00.jpg
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

Como muchos ya sabréis, [en el post de hace unas semanas vimos cómo desplegar el nuevo virtual appliance de Veeam Backup & Replication v13](https://miquelmariano.github.io/despliegue-veeam-v13-virtual-appliance-ova/). Hoy damos un paso más y vemos cómo proteger nuestras máquinas virtuales que corren sobre HPE VM Essentials (VME), gracias al nuevo Veeam Plug-in for HPE Morpheus VM Essentials.
Este plugin lleva un tiempo en beta y he tenido la suerte de probarlo en mi laboratorio. Ahora que ya está en producción, es el momento de contaros cómo funciona.

- [Parte 1 - Introducción a HPE Morpheus VM Essentials software](https://miquelmariano.github.io/introduccion-hpe-morpheus-vm-essentials-software/)
- [Parte 2 - Instalación VM Essentials software](https://miquelmariano.github.io/instalacion-nodo-vme/)
- [Parte 3 - Instalación VME Manager](https://miquelmariano.github.io/instalacion-manager/)
- [Parte 4 - Configuración inicial](https://miquelmariano.github.io/configuracion-inicial-primeros-pasos-vm-essentials)
- [Parte 5 - Creación cluster Ceph](https://miquelmariano.github.io/cluster-ceph/)
- [Parte 6 - Desplegar nuestra primera VM](https://miquelmariano.github.io/primera-vm-en-vmessentials/)
- [Parte 7 - Backups](https://miquelmariano.github.io/backups-en-vm-essentials/)
- [Parte 7.1 - Backups](https://miquelmariano.github.io/backup-vme-con-veeam/)
- [Parte 8 - Pruebas de HA](https://miquelmariano.github.io/ha-en-vm-essentials/)
- [Parte 9 - Migración de VMs desde vSphere](https://miquelmariano.github.io/migracion-vsphere-vme/)
- [Parte 9.1 - Migración con Veeam](https://miquelmariano.github.io/migracion-vsphere-vme-veeam/)
- [Parte 10 - Comandos útiles]
- [Parte 11 - Gestión de actualizaciones en HPE VM Essentials](https://miquelmariano.github.io/actualizaciones-vme-manager-y-nodos-hvm)

** ¿Qué es el Veeam Plug-in for HPE VM Essentials?

El plugin es un componente adicional que se instala sobre el servidor de Veeam Backup & Replication y que extiende sus capacidades para proteger máquinas virtuales que corren sobre el hipervisor KVM de HPE VM Essentials.
Sin este plugin, Veeam simplemente no puede descubrir ni proteger los recursos de VME. Es importante tener esto claro: no viene incluido en el instalador principal de Veeam, hay que descargarlo e instalarlo por separado.
La arquitectura es sencilla y se basa en dos componentes principales:

- Plugin module: Se instala directamente sobre el servidor de Veeam B&R. No requiere un appliance adicional. Es quien gestiona la integración, coordina los checkpoints y orquesta los jobs de backup y restore.
- Workers: Son VMs Linux ligeras que actúan como proxies para el movimiento de datos. Veeam las despliega y destruye automáticamente en cada nodo del cluster VME durante la ejecución de los jobs.

![veeam13-vme-00]({{ site.imagesposts2026 }}/06/veeams13-vme-00.jpg){: .mx-auto.d-block :}






En el post anterior vimos cómo migrar VMs desde vSphere utilizando la herramienta nativa de Migration Plans que incluye HPE VME. En esta entrega veremos una alternativa igual de válida y que en muchos entornos ya está disponible: **migrar usando Veeam Backup & Replication**.

La idea es aprovechar Veeam como vehículo de transporte. En lugar de usar el migration tool nativo, realizamos un backup de la VM en origen y la restauramos directamente sobre HPE VME mediante la opción **Full VM Restore to HPE Morpheus VM Essentials**. El resultado es el mismo, pero el proceso nos da más control y la posibilidad de partir de un punto de restauración limpio y consistente.

> ⚠️ **OJO**: Los pasos de preparación previa (inyección de drivers VirtIO) son **exactamente los mismos** que en la migración nativa. Sin estos pasos, la VM no arrancará en KVM independientemente del método de migración que usemos.

**VER TODA LA SERIE DE POSTS**

- [Parte 1 - Introducción a HPE Morpheus VM Essentials software](https://miquelmariano.github.io/introduccion-hpe-morpheus-vm-essentials-software/)
- [Parte 2 - Instalación VM Essentials software](https://miquelmariano.github.io/instalacion-nodo-vme/)
- [Parte 3 - Instalación VME Manager](https://miquelmariano.github.io/instalacion-manager/)
- [Parte 4 - Configuración inicial](https://miquelmariano.github.io/configuracion-inicial-primeros-pasos-vm-essentials)
- [Parte 5 - Creación cluster Ceph](https://miquelmariano.github.io/cluster-ceph/)
- [Parte 6 - Desplegar nuestra primera VM](https://miquelmariano.github.io/primera-vm-en-vmessentials/)
- [Parte 7 - Backups](https://miquelmariano.github.io/backups-en-vm-essentials/)
- [Parte 8 - Pruebas de HA](https://miquelmariano.github.io/ha-en-vm-essentials/)
- [Parte 9 - Migración de VMs desde vSphere](https://miquelmariano.github.io/migracion-vsphere-vme/)
- [Parte 9.1 - Migración con Veeam](https://miquelmariano.github.io/migracion-vsphere-vme-veeam/)
- [Parte 10 - Comandos útiles]
- [Parte 11 - Gestión de actualizaciones en HPE VM Essentials](https://miquelmariano.github.io/actualizaciones-vme-manager-y-nodos-hvm)

---

# Requisitos previos y preparación de la VM

La preparación previa es idéntica a la del post anterior. Resumiendo:

- Descargar el ISO de VirtIO desde [fedorapeople.org](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/virtio-win-0.1.285-1/)
- Montar el ISO en la VM y arrancar en **Windows RE** (reiniciar con `Shift` pulsado o desde `Configuración → Recuperación → Reiniciar ahora`)
- Inyectar los drivers VirtIO en la imagen de arranque:

```
dism /image:C:\ /add-driver:D:\viostor\2k22\amd64\viostor.inf
dism /image:C:\ /add-driver:D:\vioscsi\2k22\amd64\vioscsi.inf
```

- Arrancar Windows normalmente e instalar `virtio-win-gt-x64.msi` y `virtio-win-guest-tools.exe` desde la raíz del ISO
- Desmontar todos los ISOs
- Guardar la configuración de red con el script:

```powershell
.\Manage-NetworkConfig.ps1 -Action save
```

> Para más detalle sobre estos pasos, consultad el [post anterior](https://miquelmariano.github.io/migracion-vsphere-vme/).

---

# Backup final en frío

Con la VM preparada y el script de red ejecutado, el siguiente paso es **apagarla y hacer un último backup en frío**. Esto es importante porque queremos capturar el estado final de la VM ya con los drivers VirtIO instalados.

Desde Veeam, lanzar un backup bajo demanda de la VM sobre el job que la tenga asignada y esperar a que complete.

Este punto de restauración en frío será el que usemos para la migración.

---

# Restauración a HPE Morpheus VM Essentials

Veeam tiene integración nativa con HPE Morpheus VM Essentials como destino de restauración. El proceso es el siguiente.

## Iniciar el asistente

Desde la consola de Veeam, localizar el backup de la VM a migrar, hacer clic derecho y seleccionar:

`Restore entire VM → HPE Morpheus VM Essentials...`

## Virtual Machines

En el primer paso del asistente, verificar que la VM correcta está seleccionada y el restore point corresponde al backup en frío que acabamos de hacer.

## Restore Mode

Seleccionar **Restore to a new location, or with different settings**. Esta opción nos permite personalizar el cluster destino, el almacenamiento y la red, que es exactamente lo que necesitamos al cambiar de plataforma.

## Cluster

Seleccionar el cluster de HPE VME donde queremos alojar la VM. Veeam mostrará los clusters disponibles que tenga integrados como infraestructura de backup.

## Storage

Seleccionar el datastore de HPE VME donde se almacenarán los discos de la VM. Veeam mostrará los datastores disponibles en el cluster seleccionado.

## Name

Por defecto se mantiene el nombre original de la VM. Podemos cambiarlo si fuera necesario. También tenemos la opción de **Restore tags and labels** para mantener los metadatos originales.

## Network

Este paso es importante. Veeam intentará mapear automáticamente la red origen con la red destino en HPE VME. Revisar que el mapeo es correcto y ajustar si fuera necesario.

## Reason

Campo opcional para registrar el motivo de la operación. Recomendable rellenarlo con algo descriptivo como "Migración desde vSphere - [nombre VM]" para trazabilidad.

## Summary y ejecución

En la pantalla de resumen podemos revisar toda la configuración antes de ejecutar. Activar la opción **Power on target VM after restoring** si queremos que la VM arranque automáticamente al finalizar.

Hacer clic en **Finish** para iniciar la restauración. Desde el panel de **Restore session** podremos monitorizar el progreso en tiempo real.

El proceso tarda en función del tamaño de la VM. Una vez completado, el estado de la sesión pasará a **Success**.

---

# Post-migración

## Restaurar la configuración de red

Con la VM arrancada en HPE VME, abrir PowerShell como administrador y ejecutar:

```powershell
.\Manage-NetworkConfig.ps1 -Action restore
```

El script detectará el adaptador **Red Hat VirtIO Ethernet Adapter**, eliminará cualquier configuración residual y aplicará la IP, máscara, gateway y DNS guardados antes de la migración.

## VMware Tools

Al igual que en la migración nativa, Veeam tampoco desinstala VMware Tools durante el proceso de restore. Para evitar errores en el arranque:

**Opción A — Deshabilitar en el arranque** (mínimo recomendado):
`Settings → Apps → Startup → desactivar "VMware Tools Core Service"`

**Opción B — Desinstalar completamente**: Usar las herramientas recomendadas por Microsoft si la instalación está corrupta.

---

# Migración nativa vs Veeam — ¿Cuándo usar cada una?

| | Migration Plan nativo | Veeam Full VM Restore |
|---|---|---|
| **Requisito previo** | VirtIO inyectados | VirtIO inyectados |
| **Necesita Veeam** | No | Sí |
| **Backup previo** | No obligatorio | Sí (recomendado en frío) |
| **Control del proceso** | Medio | Alto |
| **Punto de restauración** | Estado live de la VM | Backup seleccionable |
| **Ideal para** | Migraciones simples | Entornos con Veeam ya desplegado |

En la práctica, si el entorno ya tiene Veeam desplegado y las VMs están siendo protegidas, la opción de Veeam es muy cómoda y añade la ventaja de poder elegir el punto de restauración concreto desde el que migrar.

---

# Conclusión

Hemos visto que Veeam nos ofrece una forma elegante y controlada de realizar la misma migración, aprovechando una infraestructura de backup que probablemente ya está operativa en el entorno. La integración de Veeam con HPE Morpheus VM Essentials como destino de restore es madura y funciona correctamente.

Los puntos clave a recordar son:

- Los drivers VirtIO son **obligatorios en ambos métodos**, no hay atajos aquí
- El backup en frío previo a la migración garantiza consistencia
- La restauración de red post-migración es necesaria en ambos casos

En el próximo post veremos los **comandos útiles** para operar el día a día de HPE VM Essentials desde la línea de comandos.

Nos vemos en el próximo post ;-)

Un saludo

Miquel.
