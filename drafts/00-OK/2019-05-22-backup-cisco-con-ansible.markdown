---
title: Backup automático de switches Cisco con Ansible
date: '2018-02-28 00:00:00'
layout: post
image: /assets/images/posts/2019/06/Cisco-and-Ansible-Happy.png
headerImage: true
tag:
- vmware
- vsphere
- vexpert
- devops
- backtobasics
category: blog
author: miquelMariano
description: Ansible playbook para automatizar el backup de nuestros switches de red Cisco, tanto catalyst como nexus...
hidden: false
comments: true
permalink: /cisco/
---

Buenos días a tod@as!!


```yaml
---

- hosts: "{{ sw }}"
  gather_facts: no
  ignore_errors: yes
  serial: 1
  vars:
    creds:
      host: "{{ host }}"
      username: "{{ username }}"
      password: "{{ password }}"
  tasks:
    - name: Create root directory if don't exist
      file:
        path: "{{ backup_folder }}"
        state: directory
        mode: 0755
    
    - name: Create individual device folder if don't exist
      file:
        path: "{{ backup_folder }}{{ inventory_hostname }}"
        state: directory
        mode: 0755

    - name: Register timestamp variable
      local_action: command date +%Y%m%d-%H:%M
      register: timestamp

    - name: Execute IOS commands
      ios_command:
        provider: "{{ creds }}"
        commands: "{{ item  }}"
      register: commands_output
      with_items:
        - show run
        - write
        - show vlan
        - show interfaces status
        - show etherchannel summary
        - show logging
        - show version
        - show spanning-tree
        - show spanning-tree blockedports
      when: 
        - cisco_os == 'ios'
    
    - name: Create IOS command folder if don't exist
      file:
        path: "{{ backup_folder }}{{ inventory_hostname }}/{{ commands_output.results[item].item }}"
        state: directory
        mode: 0755
      with_items:
        - 0
        - 1
        - 2 
        - 3
        - 4
        - 5
        - 6
        - 7
        - 8
      when:
        - cisco_os == 'ios'
    
    - name: Save IOS command output on destination file
      copy:
        content: "{{ commands_output.results[item].stdout[0] }}"
        dest:  "{{ backup_folder }}{{ inventory_hostname }}/{{ commands_output.results[item].item }}/{{ inventory_hostname }}_{{ commands_output.results[item].item }}_{{ timestamp.stdout }}.txt"
      with_items:
        - 0
        - 1
        - 2
        - 3
        - 4
        - 5
        - 6
        - 7
        - 8 
      when:
        - cisco_os == 'ios'


    - name: Execute NXOS commands
      nxos_command:
        provider: "{{ creds }}"
        commands: "{{ item  }}"
      register: commands_output
      with_items:
        - show run
        - show vlan
        - show interface status
        - show interface brief
        - show port-channel summary
        - show vpc
        - show vpc peer-keepalive
        - show logging last 100
        - copy r s
        - show version
        - show spanning-tree
        - show spanning-tree blockedports
        - show vpc consistency-parameters global
        - show cdp neighbors
        - show flogi database
        - show zoneset active
        - show fcdomain vsan 13 #Fabric1 URNIETA
        - show fcdomain vsan 24 #Fabric2 URNIETA
        - show fcdomain vsan 10 #Fabric1 TA-SA
        - show fcdomain vsan 20 #Fabric2 TA-SA
      when: 
        - cisco_os == 'nxos'

    - name: Create IOS command folder if don't exist
      file:
        path: "{{ backup_folder }}{{ inventory_hostname }}/{{ commands_output.results[item].item }}"
        state: directory
        mode: 0755
      with_items:
        - 0
        - 1
        - 2
        - 3
        - 4
        - 5
        - 6
        - 7
        - 8
        - 9
        - 10
        - 11
        - 12
        - 13
        - 14
        - 15
        - 16
        - 17
        - 18
        - 19
      when:
        - cisco_os == 'nxos' 

#    - debug: Show commands
#        var: commands_output.results[{{ item }}].item
#      with_sequence:  start=0 end=9

    - name: Save IOS command output on destination file
      copy:
        content: "{{ commands_output.results[item].stdout[0] }}"
        dest:  "{{ backup_folder }}{{ inventory_hostname }}/{{ commands_output.results[item].item }}/{{ inventory_hostname }}_{{ commands_output.results[item].item }}_{{ timestamp.stdout }}.txt"
      with_items:
        - 0
        - 1 
        - 2
        - 3
        - 4
        - 5
        - 6
        - 7
        - 8
        - 9
        - 10
        - 11
        - 12
        - 13
        - 14
        - 15
        - 16
        - 17
        - 18
        - 19
      when:
        - cisco_os == 'nxos'
```

```
all:vars]
ansible_connection=local

[CPD-1:vars]
username=admin
password=MySuperSecretPassword
backup_folder=/etc/ansible/00-backups-nexus/
cisco_os=nxos

[CPD-2:vars]
username=admin
password=MySuperSecretPassword
backup_folder=/etc/ansible/00-backups-nexus/
cisco_os=nxos

[CPD-3:vars]
username=admin
password=MySuperSecretPassword
backup_folder=/etc/ansible/00-backups-nexus/
cisco_os=nxos

[CPD-4:vars]
username=admin
password=MySuperSecretPassword
backup_folder=/etc/ansible/00-backups-catalyst/
cisco_os=ios

[CPD-1]
NX1-CPD1 host=10.30.30.76
NX2-CPD1 host=10.30.30.75

[CPD-2]
URNX01 host=10.30.30.110
URNX02 host=10.30.30.111
URNX03 host=10.30.30.112
URNX04 host=10.30.30.113

[CPD-3]
CPD3-N5K01 host=10.69.69.220
CPD3-N5K02 host=10.69.69.221
CPD3-N5K01 host=10.69.69.120
CPD3-N5K02 host=10.69.69.121

[CPD-4]
CONTROL01 host=10.30.30.181
```

Siguiendo con la serie [back-to-basics](https://miquelmariano.github.io/tags/#backtobasics), en el post de hoy veremos como eliminar ese molesto warning que se activa al habilitar SSH a nuestros ESXi.


![ssh-warning-1]({{ site.imagesposts2019 }}/05/ssh-warning-1.png)

Para poder solucionar este warning sin tener que deshabilitar de nuevo ESXi, ya que lo queremos mantener arrancado para tareas de management, tendremos que editar las opciones avanzadas del host:

![ssh-warning-2]({{ site.imagesposts2019 }}/05/ssh-warning-2.png)

Tenemos que editar la variable `UserVars.SuppressShellWarning` que por defecto está a 0 y cambiarlo a 1:

![ssh-warning-3]({{ site.imagesposts2019 }}/05/ssh-warning-3.png)

Una vez guardemos los cambios, automáticamente el warning desaparecerá:

![ssh-warning-4]({{ site.imagesposts2019 }}/05/ssh-warning-4.png)

Aprovecho también la ocación, para recordaros que hace ya tiempo, publiqué un post de [cómo manejar ESXi mediante Ansible](https://miquelmariano.github.io/2017/07/esxi-configuration-with-ansible) y que en él explicaba como configurar SSH en los ESXi mediante [este role de galaxy](https://galaxy.ansible.com/miquelMariano/ESXi_ssh)

Espero que os sirva.

Un saludo!

Miquel.


