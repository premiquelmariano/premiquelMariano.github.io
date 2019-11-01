---
title: Pendientes
date: '2000-01-01 00:00:00'
layout: post
tag:
- vmware
- vsphere
- vexpert
- devops
- backtobasics
---

https://tpetersit.blogspot.com/2018/07/vmware-horizon-75-jmp-integrated.html
https://www.myvirtualjourney.com/vmfs5-or-vmfs6/
https://jketels.nl/how-to-setup-rhel7-with-horizon-instant-clones/
https://medium.com/swlh/ansible-awx-installation-5861b115455a

## Install epel repo and then install jq
yum install -y epel-release -y && yum install jq

## Install docker-ce related packages
yum install -y yum-utils device-mapper-persistent-data lvm2

## Enable docker-ce repo and install docker engine.
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum -y install docker-ce
systemctl enable docker && systemctl start docker

## Install latest docker-compose
LATEST_VERSION=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name')
curl -L "https://github.com/docker/compose/releases/download/$LATEST_VERSION/docker-compose-$(uname -s)-$(uname -m)" > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

## Install AWX dependencies
yum install -y python2-pip
pip install ansible
pip install docker-compose

## Change dir to the home directory.
cd ~

## Get ansible-awx release tarball and extract it. 
curl \
  -o ansible-awx-6.1.0.tar.gz https://codeload.github.com/ansible/awx/tar.gz/6.1.0 && \
  tar xvfz ansible-awx-6.1.0.tar.gz && \
  rm -f ansible-awx-6.1.0.tar.gz

## Enter awx folder.  
cd awx-6.1.0

## Enter the installer directory.
cd ~/awx-6.1.0/installer

## Initiate install.yml
ansible-playbook -i inventory install.yml


https://www.howtoforge.com/ansible-awx-guide-basic-usage-and-configuration/
https://dzone.com/articles/getting-started-with-ansible-tower-hands-on


### Migrar awx a otra instancia para actualizar versión

https://github.com/ansible/awx/blob/devel/DATA_MIGRATION.md


tower-cli receive --tower-host http://192.168.6.19 --all | tower-cli send --tower-host http://192.168.6.152

 time tower-cli send --tower-host http://192.168.6.163 awx-backup/20191027-09_30_192.168.6.163.json

https://www.unixarena.com/2019/03/backup-restore-ansible-awx-tower-cli.html/

### Comandos brocade

https://thesanguy.com/2013/09/11/useful-brocade-fos-cli-commands/


