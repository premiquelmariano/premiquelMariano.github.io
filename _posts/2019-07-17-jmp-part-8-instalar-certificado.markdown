---
title: Creando un entorno JMP con VMware Horizon - Parte 8 - Instalación certificado
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

---

Buenos dias a tod@s!!

En la siguiente serie de posts, pretendo explicar durante las próximas semanas el paso a paso para instalar un entorno JMP (Just-in-Time Management Platform) utilizando VMware Horizon 7 Instant Clones + App Volumes + VMware UEM (User Environment Manager) 

- [Part 1: Introducción]({{ site.url }}/jmp-part1/)
- [Part 2: Preparar servidor SQL]({{ site.url }}/jmp-part2/)
- [Part 3: Preparar Active Directory]({{ site.url }}/jmp-part3/)
- [Part 4: Instalación y configuración Connection Server]({{ site.url }}/jmp-part4/)
- [Part 5: Instalación y configuración Replica Server]({{ site.url }}/jmp-part5/)
- [Part 6: Intalación y configuración de Security Server]({{ site.url }}/jmp-part6/)
- [Part 7: Intalación y configuración de UAG]({{ site.url }}/jmp-part7/)
    - [Part 7.1: Configuración de UAG en HA]({{ site.url }}/jmp-part7-1/)
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

# Crear certificado SSL wildcard con OpenSSL

A continuación veremos el procedimiento a seguir para generar un certificado SSL windcard emitido por una entidad certificadora pública. GoDaddy por ejemplo

* Desde cualquier equipo, instalar OpenSSL (http://gnuwin32.sourceforge.net/packages/openssl.htm)

![openssl-create-00]({{ site.imagesposts2021 }}/02/openssl-create-00.png){: .align-center}
![openssl-create-01]({{ site.imagesposts2021 }}/02/openssl-create-01.png){: .align-center}
![openssl-create-02]({{ site.imagesposts2021 }}/02/openssl-create-02.png){: .align-center}
![openssl-create-03]({{ site.imagesposts2021 }}/02/openssl-create-03.png){: .align-center}
![openssl-create-04]({{ site.imagesposts2021 }}/02/openssl-create-04.png){: .align-center}
![openssl-create-05]({{ site.imagesposts2021 }}/02/openssl-create-05.png){: .align-center}
![openssl-create-06]({{ site.imagesposts2021 }}/02/openssl-create-06.png){: .align-center}
![openssl-create-07]({{ site.imagesposts2021 }}/02/openssl-create-07.png){: .align-center}
![openssl-create-08]({{ site.imagesposts2021 }}/02/openssl-create-08.png){: .align-center}

* Crearemos un directorio de trabajo y un fichero de configuración con la información del certificado

![openssl-create-09]({{ site.imagesposts2021 }}/02/openssl-create-09.png){: .align-center}

```
[ req ]
default_bits = 2048
distinguished_name = req_distinguished_name
req_extensions = req_ext

[ req_distinguished_name ]
countryName = ES
stateOrProvinceName = Tu_Comunidad_Autonoma
localityName = Tu_Ciudad
organizationName = Nombre_organización
commonName = *.tudominio.com

[ req_ext ]
subjectAltName = @alt_names
[alt_names]
DNS.1 = *.tudominio.com
DNS.2 = tudominio.com
```

* Generar CSR en base al certificado deseado. 

Ejecutaremos el siguiente comando:

`openssl req -new -keyout <your.domain.com>.key -out <your.domain.com>.csr -nodes -newkey rsa:4096 -config <path>/openssl.cnf`

Es necesario que volvamos a introducir los datos de configuración ya que de lo contrario, recibiremos un error.

![openssl-create-10]({{ site.imagesposts2021 }}/02/openssl-create-10.png){: .align-center}

A continuación vemos los ficheros que acabamos de generar.

![openssl-create-11]({{ site.imagesposts2021 }}/02/openssl-create-11.png){: .align-center}

* Solicitar certificado a nuestra entidad certificadora.
En mi caso, el certificado lo he creado en GoDaddy y una vez generado, nos podremos descargar el .zip con los certificados públicos.

![openssl-create-12]({{ site.imagesposts2021 }}/02/openssl-create-12.png){: .align-center}

* Combinar clave pública con clave privada

Con el siguiente comando, podremos combinar el certificado de la CA .crt con la clave privada generada inicialmente .key

`OpenSSL.exe pkcs12 -export -out <your.domain.com>.p12 -inkey <your.domain.com>.key -in "c41a3a446823203d.crt"`

Se puede generar el certificado en formato .p12 o .pfx

Al combinar ambos ficheros, nos pedirá una contraseña. Esta contraseña será de vital importancia, ya que se nos requerirá a la hora de instalar el certificado en los servidores de conexión de Horizon o los UAG.

![openssl-create-13]({{ site.imagesposts2021 }}/02/openssl-create-13.png){: .align-center}

# Instalación de certificado wildcard en Connection Server

![certificado-connection-server-01]({{ site.imagesposts2020 }}/02/certificado-connection-server-01.png){: .align-center}
![certificado-connection-server-02]({{ site.imagesposts2020 }}/02/certificado-connection-server-02.png){: .align-center}
![certificado-connection-server-03]({{ site.imagesposts2020 }}/02/certificado-connection-server-03.png){: .align-center}
![certificado-connection-server-04]({{ site.imagesposts2020 }}/02/certificado-connection-server-04.png){: .align-center}
![certificado-connection-server-05]({{ site.imagesposts2020 }}/02/certificado-connection-server-05.png){: .align-center}
![certificado-connection-server-06]({{ site.imagesposts2020 }}/02/certificado-connection-server-06.png){: .align-center}
![certificado-connection-server-07]({{ site.imagesposts2020 }}/02/certificado-connection-server-07.png){: .align-center}
![certificado-connection-server-08]({{ site.imagesposts2020 }}/02/certificado-connection-server-08.png){: .align-center}
![certificado-connection-server-09]({{ site.imagesposts2020 }}/02/certificado-connection-server-09.png){: .align-center}
![certificado-connection-server-10]({{ site.imagesposts2020 }}/02/certificado-connection-server-10.png){: .align-center}
![certificado-connection-server-11]({{ site.imagesposts2020 }}/02/certificado-connection-server-11.png){: .align-center}
![certificado-connection-server-12]({{ site.imagesposts2020 }}/02/certificado-connection-server-12.png){: .align-center}
![certificado-connection-server-13]({{ site.imagesposts2020 }}/02/certificado-connection-server-13.png){: .align-center}
![certificado-connection-server-14]({{ site.imagesposts2020 }}/02/certificado-connection-server-14.png){: .align-center}
![certificado-connection-server-15]({{ site.imagesposts2020 }}/02/certificado-connection-server-15.png){: .align-center}
![certificado-connection-server-16]({{ site.imagesposts2020 }}/02/certificado-connection-server-16.png){: .align-center}
![certificado-connection-server-17]({{ site.imagesposts2020 }}/02/certificado-connection-server-17.png){: .align-center}
![certificado-connection-server-18]({{ site.imagesposts2020 }}/02/certificado-connection-server-18.png){: .align-center}
![certificado-connection-server-19]({{ site.imagesposts2020 }}/02/certificado-connection-server-19.png){: .align-center}
![certificado-connection-server-20]({{ site.imagesposts2020 }}/02/certificado-connection-server-20.png){: .align-center}
![certificado-connection-server-21]({{ site.imagesposts2020 }}/02/certificado-connection-server-21.png){: .align-center}

# Instalación de certificado wildcard en Unified Access Gateway

![certificado-uag-01]({{ site.imagesposts2020 }}/02/certificado-uag-01.png){: .align-center}
![certificado-uag-02]({{ site.imagesposts2020 }}/02/certificado-uag-02.png){: .align-center}
![certificado-uag-03]({{ site.imagesposts2020 }}/02/certificado-uag-03.png){: .align-center}
![certificado-uag-04]({{ site.imagesposts2020 }}/02/certificado-uag-04.png){: .align-center}


Espero que os sirva.

Un saludo!

Miquel.


