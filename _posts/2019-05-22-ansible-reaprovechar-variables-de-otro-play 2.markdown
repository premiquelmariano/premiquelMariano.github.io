---
title: ¿Cómo pasar variables de un play a otro con Ansible?
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

```yaml
---
##EXAMPLE:  ansible-playbook playbooks/win_update.yml -i inventory/servers -e "servers=dc install_updates=false"

##############################################################################
## Play 1   Search-only, return list of found updates (if any).
##############################################################################
- hosts: "{{ servers }}"
  tasks:
    - name: Search-only, return list of found updates (if any).
      win_updates:
        category_names:
          - SecurityUpdates
          - CriticalUpdates
          - UpdateRollups
        state: searched
      register: list_of_found_updates

    - debug:
        var: list_of_found_updates

#    - debug:
#        var: groups[ "{{ servers }}" ]

##############################################################################
### Play 2   Send info with telegram
##############################################################################
- hosts: localhost
  connection: local
  tasks:
    - name: Send telegram notification
      telegram:
        token: 304017237:AAHpKXZBaw_wOF3H-ryhWl3F3wqIVP_Zqf8
        chat_id: 6343788
        msg: Host "{{ hostvars[item].inventory_hostname }}" >> "{{ hostvars[item].list_of_found_updates.found_update_count }}" found updates.
# "{{ hostvars[item].list_of_found_updates.results[0].found_update_count }}" "{{ hostvars[item].list_of_found_updates.results[0].item }}" "{{ hostvars[item].list_of_found_updates.results[1].found_update_count }}" "{{ hostvars[item].list_of_found_updates.results[1].item }}" "{{ hostvars[item].list_of_found_updates.results[2].found_update_count }}" "{{ hostvars[item].list_of_found_updates.results[2].item }}"
      with_items:
        -  "{{ groups[servers] }}"
      ignore_errors: yes


##############################################################################
#### Play 3    Install all security, critical, and rollup updates when install_updates is true
###############################################################################
- hosts: "{{ servers }}"
  tasks:
    - name: Install all security, critical, and rollup updates
      win_updates:
        category_names:
          - SecurityUpdates
          - CriticalUpdates
          - UpdateRollups
        reboot: yes
      when:
          - install_updates == true
```



Espero que os sirva.

Un saludo!

Miquel.


