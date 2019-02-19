---
title: PowerCLI, comandos útiles sin scripts
date: '2017-09-22 00:00:00'
layout: post
image: /assets/images/posts/2019/02/onliners-banner.jpg
headerImage: true
tag:
- vexpert
- automation
- vsphere
- vmware
category: blog
author: miquelMariano
description: Hoy, me gustaría compartir con vosotros una lista de commandos que podemos ejecutar sin necesidad de crear ningún script y que nos dan información muy valiosa de nuestro entorno vsphere
hidden: false
comments: true
permalink: /onliners/
---


Lista de VMs con snapshots

Get-VM | Get-Snapshot | where {$_.Name -notmatch "Restore Point \w"} | Select VM,Name,Description,@{Label="Size";Expression={"{0:N2} GB" -f ($_.SizeGB)}},Created | FT -Autosize

Lista de VMs con CD montado

Get-VM | Get-CDDrive | Where-Object {$_.IsoPath -ne $null} | Select Parent,IsoPath 

Desmontar todas las ISOs montadas en todas las VMs

Get-VM | Get-CDDrive | where {$_.IsoPath -ne $null} | Set-CDDrive -NoMedia -Confirm:$False

Ver estado del servicio SSH

Get-VMHost | Get-VMHostService | Where { $_.Key -eq "TSM-SSH" } |select VMHost, Label, Running

Arrancar servicio SSH

Get-VMHost | Foreach {Start-VMHostService -HostService ($_ | Get-VMHostService | Where { $_.Key -eq "TSM-SSH"} )}

Apagar servicio SSH

Get-VMHost | Foreach {stop-VMHostService -HostService ($_ | Get-VMHostService | Where { $_.Key -eq "TSM-SSH"} )}

Contar numero de VMs por host

Get-VMHost | Sort-Object Name | Select Name,@{N="VM";E={ if ($_.ExtensionData.Vm -ne $null) { $_.ExtensionData.Vm.Count } else {0}}}

Contar numero de VMs por datastore

Get-datastore | Sort-Object Name | Select Name,@{N="VM";E={ if ($_.ExtensionData.Vm -ne $null) { $_.ExtensionData.Vm.Count } else {0}}}

Ver información hardware de los ESXi

Get-VMHost |Sort Name |Get-View | Select Name, @{N=“Type“;E={$_.Hardware.SystemInfo.Vendor+ “ “ + $_.Hardware.SystemInfo.Model}}, @{N=“CPU“;E={“PROC:“ + $_.Hardware.CpuInfo.NumCpuPackages + “CORES:“ + $_.Hardware.CpuInfo.NumCpuCores + “ MHZ: “ +[math]::round($_.Hardware.CpuInfo.Hz / 1000000, 0)}}, @{N=“MEM“;E={“” + [math]::round($_.Hardware.MemorySize / 1GB, 0) + “GB“}} | FT -autosize

Ver estado de las VMware Tools y Virtual Hardware de las VMs encendidas.

Get-VM | Select @{N=”VMName”; E={$_.Name}}, @{N=”State”; E={$_.PowerState}},  @{N=”HardwareVersion”; E={$_.Extensiondata.Config.Version}}, @{N=”ToolsVersion”; E={$_.Extensiondata.Config.Tools.ToolsVersion}}, @{N=”ToolsStatus”; E={$_.Extensiondata.Summary.Guest.ToolsStatus}}, @{N=”ToolsVersionStatus”; E={$_.Extensiondata.Summary.Guest.ToolsVersionStatus}}, @{N=”ToolsRunningStatus”; E={$_.Extensiondata.Summary.Guest.ToolsRunningStatus}} | where state -notmatch poweredoff | FT

Ver las VMs que se han creado recientemente

Get-VIEvent -maxsamples 10000 | Where {$_.Gettype().Name -eq "VmCreatedEvent"} | Select createdTime, UserName, FullFormattedMessage

Ver las VMs que se han eliminado recientemente

Get-VIEvent -maxsamples 10000 | Where {$_.Gettype().Name -eq "VmRemovedEvent"} | Select createdTime, UserName, FullFormattedMessage

Ver errores de la última semana

Get-VIEvent -maxsamples 10000 -Type Error -Start (get-date).AddDays(-7) | Select createdTime, fullFormattedMessage

Ver VMs con la nic e1000

get-vm | Get-NetworkAdapter | where {$_.type -match "e1000"} | select-object parent,networkname,name,type




![ps6-13]({{ site.imagesposts2019 }}/01/PowerShell6-13.png)

Espero que os sea de utilidad.

Un saludo!

Miquel.


