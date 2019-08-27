---
title: Creando un entorno JMP con VMware Horizon - Parte 9
date: '2019-07-17 00:00:00'
layout: post
image: /assets/images/posts/2019/07/horizon-logo.png
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
permalink: /jmp-part7/

---

https://www.carlstalhood.com/vmware-unified-access-gateway/

Buenos días a tod@s!!

En la siguiente serie de posts, pretendo explicar durante las próximas semanas el paso a paso para instalar un entorno JMP (Just-in-Time Management Platform) utilizando VMware Horizon 7 Instant Clones + App Volumes + VMware UEM (User Environment Manager) 

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server]({{ site.url }}/jmp-part5/)
- [Part 6: Instalación y configuración de Security Server]({{ site.url }}/jmp-part6/)
- [Part 7: Instalación y configuración de UAG]({{ site.url }}/jmp-part7/)
- [Part 8: Instalación certificado (opcional)]({{ site.url }}/jmp-part8/)
- [Part 9: Preparar plantilla master para Instant Clone]({{ site.url }}/jmp-part9/)
- [Part 10: Configurar un pool de Instant Clone]({{ site.url }}/jmp-part10/)
- [Part 11: Instalar App Volumes]({{ site.url }}/jmp-part11/)
- [Part 12: Configuración inicial App Volumes]({{ site.url }}/jmp-part12/)
- [Part 13: Crear nuestro primer App Stack]({{ site.url }}/jmp-part13/)
- [Part 14: Trabajando con Writable Volumes]({{ site.url }}/jmp-part14/)
- [Part 15: User Environment Manager Installation]({{ site.url }}/jmp-part15/)
- [Part 16: Primeros pasos con UEM]({{ site.url }}/jmp-part16/)
- [Part 17: Instalación y configuración JMP Server]({{ site.url }}/jmp-part17/)
- [Part 18: Aprovisionamiento con JMP]({{ site.url }}/jmp-part18/)

# Instalación y configuración de UAG (Unified Access Gateway)

Unified Access Gateway (UGA) es un componente dentro de la infraestructura Horizon que nos proveerá de conectividad remota hacia nuestros escritorios VDI

![uag0]({{ site.imagesposts2019 }}/09/uag0.png){: .align-center}

UAG, viene a reemplazar los [ya conocidos Horizon Security Servers]({{ site.url }}/jmp-part6/) y algunos de los beneficios que nos aportan son:

* El emparejamiento ya no es 1:1 como se hacia con la topología de Security Server. Con UAG, un único appliance puede estar emparejado a múltiples connections servers a través de un balanceador.

* La conectividad entre UAG y connection server solo requiere del puerto TCP443 lo que simplifica muchísimo las reglas a nivel de firewall. Eso si, seguiremos necesitando los puertos 4172, 22443, etc. hacia los Horizon Agents.

* Adicionalmente y para una mayor securización, UAG soporta métodos de autenticación como RSA SecurID, Radius, CAC, etc...

Con todo lo que he expuesto anteriormente, no quiero dar a entender que Horizon Security Server ya no se pueda utilizar. Sigue siendo un producto válido que VMware sigue desarrollando y soportando.
{: .notice}

### Configuración firewall

En el siguiente esquema, podreis ver una representación de la topología para dar acceso a nuestro entorno VDI desde internet

![uag3]({{ site.imagesposts2019 }}/09/uag3.png){: .align-center}

Los puertos necesarios para la correcta configuración son los siguientes, y están sacados de la [documentación oficial:](https://docs.vmware.com/en/Unified-Access-Gateway/3.6/com.vmware.uag-36-deploy-config.doc/GUID-F197EB60-3A0C-41DF-8E3E-C99CCBA6A06E.html)

Acceso desde cualquier dispositivo de internet hacia el UAG appliance o balanceador:

* TCP and UDP 443 (incluye Blast Extreme)
* TCP and UDP 4172. UDP 4172 debe estar permitido en ambas direcciones. (PCoIP)
* TCP and UDP 8443 (para HTML Blast)

Acceso desde los UAG appliance hacia los connection servers:

* TCP 443 

Acceso desde los UAG appliance hacia los escritorios:

* TCP and UDP 4172 (PCoIP). UDP 4172 debe estar permitido en ambas direcciones.
* TCP 32111 (USB Redirection) 
* TCP and UDP 22443 (Blast Extreme) 
* TCP 9427 (MMR and CDR) 

### Despliegue OVA

![uag1]({{ site.imagesposts2019 }}/09/uag1.png){: .align-center}
![uag2]({{ site.imagesposts2019 }}/09/uag2.png){: .align-center}

### Interfaz de administración

![uag4]({{ site.imagesposts2019 }}/09/uag4.png){: .align-center}
![uag5]({{ site.imagesposts2019 }}/09/uag5.png){: .align-center}
![uag6]({{ site.imagesposts2019 }}/09/uag6.png){: .align-center}
![uag7]({{ site.imagesposts2019 }}/09/uag7.png){: .align-center}
![uag8]({{ site.imagesposts2019 }}/09/uag8.png){: .align-center}
![uag9]({{ site.imagesposts2019 }}/09/uag9.png){: .align-center}
![uag10]({{ site.imagesposts2019 }}/09/uag10.png){: .align-center}
![uag11]({{ site.imagesposts2019 }}/09/uag11.png){: .align-center}
![uag12]({{ site.imagesposts2019 }}/09/uag12.png){: .align-center}
![uag13]({{ site.imagesposts2019 }}/09/uag13.png){: .align-center}
![uag14]({{ site.imagesposts2019 }}/09/uag14.png){: .align-center}
![uag15]({{ site.imagesposts2019 }}/09/uag15.png){: .align-center}

Y hasta aquí por hoy, en el próximo post veremos cómo crear nuestro primer Pool de Linked Clones

Espero que os sirva.

Nos vemos en el próximo post: [Part 10: Configurar un pool de Instant Clone]({{ site.url }}/jmp-part10/)

Un saludo!

Miquel.


