---
title: 100 preguntas y respuestas sobre Ansible que quizás desconoces. (Parte1)
date: '2018-02-28 00:00:00'
layout: post
image: /assets/images/posts/2019/05/ansible-logo.png
headerImage: true
tag:
- vmware
- vsphere
- vexpert
- devops
- backtobasics
category: blog
author: miquelMariano
description: En este post vamos a ver los contadores mas importantes de CPU que nos podemos encontrar en cada VM de nuestro entorno.
hidden: false
comments: true
permalink: /ansible100/
---

https://www.knowledgehut.com/interview-questions/ansible

https://www.wisdomjobs.com/e-university/ansible-software-interview-questions.html

https://www.algrim.co/posts/142-ansible-interview-questions#q-14

http://aptronnoida.in/iqa/best-ansible-interview-questions-answers/

https://smconsultant.com/ansible-interview-question-and-answers/



Buenos dias a tod@as!!

Hace ya tiempo que tengo en mente escribir esta serie de posts, y es que cada vez más, la gente se va interesendo por la automatización de tareas en general y Ansible en particular.

La idea es publicar una serie de posts en donde intentaré resolver de forma clara y directa las preguntas que os puesan venir a la cabeza sobre el mundo Ansible, ahi va, espero os guste:

- [Parte1 (usted está aquí)](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)
- [part1](https://miquelmariano.github.io)

## 1. ¿Qué es Ansible?

Ansible es una herramienta que nos permite llevar un control sobre la gestión de la configuración y su automatización. Está escrito en Python.

Su web obicial es [www.ansible.com](https://www.ansible.com/)

## x. ¿Por qué automatizar?

- Por la disminución y menor posibilidad de errores
Siento ser tan directo y deciros esto, pero cometéis errores, cometemos errores. Todos lo hacemos Continuamente, los humanos, malinterpretamos las cosas, leemos mal, nos olvidamos de algunas tareas, hacemos las tareas en el orden equivocado...Eso es así, y es por eso que la automatización nos permite salirnos de la ecuación y dejar que los sistemas hagan por si solos.
- Por el ahorro de tiempo
Todo lleva tiempo: iniciar sesión en consolas, buscar configuraciones, conectarse a servidores, escribir comandos. Especialmente cuando, según el punto anterior, arruinamos algo y tenemos que arreglarlo. Una vez más, simplemente dejemos que los sistemas lo hagan. Dediquemos nuestro tiempo a innovar, a pensar cómo automatizar mas cosas.
- Por la auto documentación
En nuestro día a día, estamos acostumbrados a tratar con infinidad de documentación de instalación y configuración de nuestros sistemas, tareas y operaciones. Esta documentación requiere de un gran esfuerzo para mantenerla actualizada e inevitablemente en muchos casos se descuida y entra en desuso. Infrastructure as Code / Programmable Infrastructure son conceptos que nos permiten a través de código tener una visión clara tanto de la configuración como de la implementación de un sistema o tarea con sus pasos a seguir bien definidos. Además, en muchos casos, la configuración inicial y el ciclo de vida de un sistema se automatiza. De esta forma siempre tenemos el código con la configuración actual sin necesidad de mantener documentación paralela.
- Por la reproducibilidad
Reproducibilidad significa que tenemos que ser capaces de reproducir o recrear nuestro sistema de manera fácil y rápida.
Se nos puede dar el caso que queramos un entorno paralelo de pruebas para probar nuestros desarrollos o poniéndonos en lo peor, podríamos perder todo nuestro sistema.
Tenemos un servicio X que funciona perfectamente, pero el día menos pensado tenemos una contingencia grave y se pierde todo.
Tenemos los datos bien salvaguardados en copias de seguridad, pero hay que montar de nuevo toda la infraestructura y la persona que en su día se encargó ya no está en la empresa y sólo dejo un documento básico de instalación. Seguimos ese documento al pie de la letra, pero no hay manera de que eso funcione L
Con la automatización y la Infrastructure as Code que comentábamos antes eso es posible, ya que tenemos el código con la última configuración de ese sistema y seriamos capaces de repetir esas configuraciones tantas veces cómo nos sea necesario.

## 2. ¿Cuales son las ventajas de Ansible?

- Es agent-less, es decir, no requiere de instalación de agentes en los servidores a controlar
- Simplicidad
- Buen rendimiento
- Bajo overhead

## x. ¿Que precio tiene Ansible?

## x. ¿Que es Tower?

## x. ¿Dónde se puede instalar?

## x. ¿Cómo instalo Ansible?


Question 3. How Ansible Works?

Answer :

There are many similar automation tools available like Puppet, Capistrano, Chef, Salt, Space Walk etc, but Ansible categorize into two types of server: controlling machines and nodes.

The controlling machine, where Ansible is installed and Nodes are managed by this controlling machine over SSH. The location of nodes are specified by controlling machine through its inventory.

The controlling machine (Ansible) deploys modules to nodes using SSH protocol and these modules are stored temporarily on remote nodes and communicate with the Ansible machine through a JSON connection over the standard output.

How Ansible Works:

Ansible is agent-less, that means no need of any agent installation on remote nodes, so it means there are no any background daemons or programs are executing for Ansible, when it’s not managing any nodes.

Ansible can handle 100’s of nodes from a single system over SSH connection and the entire operation can be handled and executed by one single command ‘ansible’. But, in some cases, where you required to execute multiple commands for a deployment, here we can build playbooks.

Playbooks are bunch of commands which can perform multiple tasks and each playbooks are in YAML file format.


 
Question 4. What’s The Use Of Ansible?

Answer :

Ansible can be used in IT infrastructure to manage and deploy software applications to remote nodes. For example, let’s say you need to deploy a single software or multiple software to 100’s of nodes by a single command, here ansible comes into picture, with the help of Ansible you can deploy as many as applications to many nodes with one single command, but you must have a little programming knowledge for understanding the ansible scripts.

We’ve compiled a series on Ansible, title ‘Preparation for the Deployment of your IT Infrastructure with Ansible IT Automation Tool‘, through parts 1-4 and covers the following topics.

Question 5. Is There A Web Interface / Rest Api / Etc?

Answer :

Yes, Ansible, Inc makes a great product that makes Ansible even more powerful and easy to use. See Ansible Tower.

Question 6. How Do I Submit A Change To The Documentation?

Answer :

Documentation for Ansible is kept in the main project git repository, and complete instructions for contributing can be found in the docs.


 
Question 7. When Should I Use {{ }}? Also, How To Interpolate Variables Or Dynamic Variable Names?

Answer :

A steadfast rule is ‘always use {{ }} except when when:‘. Conditionals are always run through Jinja2 as to resolve the expression, so when: failed_when: and changed_when: are always templated and you should avoid adding {{}}.

In most other cases you should always use the brackets, even if previouslly you could use variables without specifying (like with_ clauses), as this made it hard to distinguish between an undefined variable and a string.

Another rule is ‘moustaches don’t stack’. We often see this:

{{ somevar_{{other_var}} }}

The above DOES NOT WORK, if you need to use a dynamic variable use the hostvars or vars dictionary as appropriate:

{{ hostvars[inventory_hostname]['somevar_' + other_var] }}

Question 8. How To Install Ansible?

Answer :

Installation of Ansible Ubuntu 14.04

The best way to get Ansible for Ubuntu is to add the project’s PPA (personal package archive) to your system.

To do this effectively, we need to install the software-properties-common package, which will give us the ability to work with PPAs easily. (This package was called python-software-properties on older versions of Ubuntu.)

sudo apt-get update
sudo apt-get install software-properties-common
Once the package is installed, we can add the Ansible PPA by typing the following command:

sudo apt-add-repository ppa:ansible/ansible

Press ENTER to accept the PPA addition.

Next, we need to refresh our system’s package index so that it is aware of the packages available in the PPA. Afterwards, we can install the software:

sudo apt-get update
sudo apt-get install ansible
We now have all of the software required to administer our servers through Ansible.
Question 9. How Do I Generate Crypted Passwords For The User Module?

Answer :

The mkpasswd utility that is available on most Linux systems is a great option:

mkpasswd --method=sha-512

If this utility is not installed on your system (e.g. you are using OS X) then you can still easily generate these passwords using Python. First, ensure that the Passlib password hashing library is installed.

pip install passlib

Once the library is ready, SHA512 password values can then be generated as follows:

python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"

Use the integrated Hashing filters to generate a hashed version of a password. You shouldn’t put plaintext passwords in your playbook or host_vars; instead, use Vault to encrypt sensitive data.


 
Question 10. Desired To Gain Proficiency On Ansible?

Answer :

Explore the blog post on Ansible training to become a pro in Ansible.

Question 11. How Do I Get Ansible To Reuse Connections, Enable Kerberized Ssh, Or Have Ansible Pay Attention To My Local Ssh Config File?

Answer :

Switch your default connection type in the configuration file to ‘ssh’, or use ‘-c ssh’ to use Native OpenSSH for connections instead of the python paramiko library. In Ansible 1.2.1 and later, ‘ssh’ will be used by default if OpenSSH is new enough to support ControlPersist as an option.

Paramiko is great for starting out, but the OpenSSH type offers many advanced options. You will want to run Ansible from a machine new enough to support ControlPersist, if you are using this connection type. You can still manage older clients. If you are using RHEL 6, CentOS 6, SLES 10 or SLES 11 the version of OpenSSH is still a bit old, so consider managing from a Fedora or openSUSE client even though you are managing older nodes, or just use paramiko.

We keep paramiko as the default as if you are first installing Ansible on an EL box, it offers a better experience for new users.

Question 12. What Is The Best Way To Make Content Reusable/redistributable?

Answer :

If you have not done so already, read all about “Roles” in the playbooks documentation. This helps you make playbook content self-contained, and works well with things like git submodules for sharing content with others.

If some of these plugin types look strange to you, see the API documentation for more details about ways Ansible can be extended.


 
Question 13. How Do I See All The Inventory Vars Defined For My Host?

Answer :

You can see the resulting vars you define in inventory running the following command:

ansible -m debug -a "var=hostvars['hostname']" localhost.

Question 14. How Do I Copy Files Recursively Onto A Target Host?

Answer :

The “copy” module has a recursive parameter, though if you want to do something more efficient for many files, look at the “synchronize” module instead, which wraps rsync. See the module index for info on both modules.

Question 15. What Is Ansible Role?

Answer :

Ansible can interact with configured clients from the command line with the ansible command, and how you can automate configuration with playbooks run through the ansible-playbook command.

The first step in creating a role is creating its directory structure. To create the base directory structure, we’re going to use a tool bundled with Ansible called ansible-galaxy:

$ ansible-galaxy init azavea.packer
azavea.packer was created successfully
That command will create an azavea.packer directory with the following structure:

+-- README.md

+-- defaults

¦ +-- main.yml

+-- files

+-- handlers

¦ +-- main.yml

+-- meta

¦ +-- main.yml

+-- tasks

¦ +-- main.yml

+-- templates

+-- vars

+-- main.yml


 
Question 16. How Do I Access A Variable Name Programmatically?

Answer :

An example may come up where we need to get the ipv4 address of an arbitrary interface, where the interface to be used may be supplied via a role parameter or other input. Variable names can be built by adding strings together, like so:

{{ hostvars[inventory_hostname]['ansible_' + which_interface]['ipv4']['address'] }}

The trick about going through hostvars is necessary because it’s a dictionary of the entire namespace of variables. ‘inventory_hostname’ is a magic variable that indicates the current host you are looping over in the host loop.

Question 17. How Do I Access Shell Environment Variables?

Answer :

If you just need to access existing variables, use the ‘env’ lookup plugin.

For example, to access the value of the HOME environment variable on management machine:

---

# ...

 vars:

   local_home: "{{ lookup('env','HOME') }}"

If you need to set environment variables, see the Advanced Playbooks section about environments.

Ansible 1.4 will also make remote environment variables available via facts in the ‘ansible_env’ variable:

{{ ansible_env.SOME_VARIABLE }}

Un saludo!

Miquel.


