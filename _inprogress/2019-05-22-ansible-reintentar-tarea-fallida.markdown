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

https://coderwall.com/p/ww4dxw/ansible-retry-task

```yaml
---
- hosts: all
  connection: local
  tasks:
      - shell: exit 1
        register: task_result
        until: task_result.rc == 0
        retries: 10
        delay: 1
        ignore_errors: yes
```

![ansible-retry]({{ site.imagesposts2019 }}/07/ansible-retry.png)


Espero que os sirva.

Un saludo!

Miquel.


