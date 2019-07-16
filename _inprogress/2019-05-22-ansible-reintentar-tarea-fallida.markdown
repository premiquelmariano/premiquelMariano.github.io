---
title: Reintentar tarea fallida en Ansible
date: '2018-02-28 00:00:00'
layout: post
image: 
  path: /assets/images/posts/2019/06/Cisco-and-Ansible-Happy.png
  thumbnail: /assets/images/posts/2019/06/Cisco-and-Ansible-Happy.png
tag:
- vmware
- vsphere
- vexpert
- devops
- backtobasics

---

Muchas veces, cuando trabajamos con tareas de Ansible nos encontramos que en más de una ocasión, la acción falla.

Evidentemente, si este fallo es debido a una mala configuración del servidor o que Ansible no se encuentra con el estado esperado, tendremos que revisar qué está pasando para poder solucionaro.

En cambio, muchas otras veces, este error es temporal, o bien porque el servidor de destino está ocupado y no puede procesar la operación o simplemente porque se ha dado algún tipo de timeout y simplemente reintentando la tarea, ésta funcionará correctamente.

Para poder reintentar una tarea de Ansible de forma automática, bastará con poner la opción `retries: xx` dónde `xx` será el número de intentos a hacer. También podemos poner la opción `delay: xx` para indicar cuanto tiempo dejará pasar entre intento y intento.

```yaml
---
- hosts: ESXi
  connection: local
  tasks:
    - name: Unmount datastores ESXi
      command: "{{ item }}"
      register: task_result
      until: task_result.rc == 0
      retries: 3
      delay: 10
      with_items:
        - esxcli storage filesystem unmount -l IX_Simplex000_LDEV3000
        - esxcli storage filesystem unmount -l IX_Simplex001_LDEV3001
        - esxcli storage filesystem unmount -l IX_Simplex002_LDEV3002
        - esxcli storage filesystem unmount -l IX_Simplex003_LDEV3003
        - esxcli storage filesystem unmount -l IX_Simplex004_LDEV3004
      when: "'loggs' in inventory_hostname "
      tags: unmount
```


![ansible-retry]({{ site.imagesposts2019 }}/07/ansible-retry.png)


Espero que os sirva.

Un saludo!

Miquel.


