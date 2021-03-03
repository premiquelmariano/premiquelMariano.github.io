---
title: Configurar VMware Horizon con doble factor de autenticación 2FA MFA
date: '2021-01-22 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- vmware
- horizon
- vexpert
- euc
- desktop
- mobility
- mfa
- 2fa
- mfa
- duo
- security
---

En el post de hoy hablaremos de DUO Security, un servicio cloud para dotar de doble factor de autenticación a nuestras aplicaciones. Veremos cómo se hace la configuración básica y cómo podemos proteger nuestro entorno VDI con MFA.

# DUO Security MFA

Extraído de su propia [página web](https://duo.com/product/multi-factor-authentication-mfa) 

DUO Securtiy nos aporta una autenticación multifactor moderna y eficaz
La autenticación multifactor de Duo de Cisco protege sus aplicaciones mediante el uso de una segunda fuente de validación, como un teléfono o un token, para verificar la identidad del usuario antes de otorgar acceso. Duo está diseñado para proporcionar una experiencia de inicio de sesión simple y optimizada para cada usuario y aplicación, y como solución basada en la nube, se integra fácilmente con su tecnología existente. 

![duo-02]({{ site.imagesposts2021 }}/03/duo-02.png){: .align-center}

Cómo cualquier servicio cloud, está basado en el pago por uso y la parte buena de DUO es que tiene una versión gratuita para 10 usuarios. Perfecto para realizar nuestros laboratorios y demos

![duo-01]({{ site.imagesposts2021 }}/03/duo-01.png){: .align-center}

# Instalación DUO Authentication Proxy

Una vez nos hayamos registrado en el portal de DUO, el primer paso será conectar nuestro entorno on-premise con la cuenta cloud.

![duo-install-00]({{ site.imagesposts2021 }}/03/duo-install-00.png){: .align-center}

En el [este enlace](https://duo.com/docs/checksums#duo-authentication-proxy) encontraremos todos los binarios para windows y para linux. Es un instalador siguiente > siguiente > fin.

![duo-install-01]({{ site.imagesposts2021 }}/03/duo-install-01.png){: .align-center}
![duo-install-02]({{ site.imagesposts2021 }}/03/duo-install-02.png){: .align-center}
![duo-install-03]({{ site.imagesposts2021 }}/03/duo-install-03.png){: .align-center}

Toda la configuración se encuentra en el fichero `C:\Program Files\Duo Security Authentication Proxy\conf\authproxy.cfg`

La configuración que viene por defecto se puede borrar, ya que solo son ejemplos

![duo-install-04]({{ site.imagesposts2021 }}/03/duo-install-04.png){: .align-center}

## Configuración SSO con Active Directory

Aquí es dónde configuraremos la conexión de nuestro proxy recién instalado con la cuenta de DUO. 

Single Sign-On > Add source > Add an Acrive Directory > Add Authentication Proxy

![duo-install-05]({{ site.imagesposts2021 }}/03/duo-install-05.png){: .align-center}
![duo-install-06]({{ site.imagesposts2021 }}/03/duo-install-06.png){: .align-center}
![duo-install-07]({{ site.imagesposts2021 }}/03/duo-install-07.png){: .align-center}
![duo-install-08]({{ site.imagesposts2021 }}/03/duo-install-08.png){: .align-center}

Con el proxy ya configurado, haremos la configuración de nuestro Active Directory

![duo-install-09]({{ site.imagesposts2021 }}/03/duo-install-09.png){: .align-center}
![duo-install-10]({{ site.imagesposts2021 }}/03/duo-install-10.png){: .align-center}

Todo el detalle de la config está en esta [documentación oficial](https://duo.com/docs/sso#enable-duo-single-sign-on)

## Sincronizar usuarios AD

Con la configuración de nuestro SSO es el momento de sincronizar nuestros usuarios del directorio activo

![duo-install-11]({{ site.imagesposts2021 }}/03/duo-install-11.png){: .align-center}

Asignaremos un nombre a nuestro registro y configuraremos el Proxy para que se conecte con nuestro AD

![duo-install-12]({{ site.imagesposts2021 }}/03/duo-install-12.png){: .align-center}

Los datos de configuración los tendremos que configurar en el fichero de configuración del proxy y para mayor comodidad, el propio asistente nos deja descargar ese fichero pre-configurado.

![duo-install-13]({{ site.imagesposts2021 }}/03/duo-install-13.png){: .align-center}
![duo-install-14]({{ site.imagesposts2021 }}/03/duo-install-14.png){: .align-center}

Es importante que después de cualquier modificación en el fichero de configuración se reinicie el servicio.

Terminamos con la configuración del AD

![duo-install-15]({{ site.imagesposts2021 }}/03/duo-install-15.png){: .align-center}
![duo-install-16]({{ site.imagesposts2021 }}/03/duo-install-16.png){: .align-center}

## Enroll Users

Una vez tengamos nuestros usuarios ya sincronizados con DUO, es el momento de enviarles las instrucciones para que se activen y cada usuario pueda instalar la aplicación móvil.

![duo-install-17]({{ site.imagesposts2021 }}/03/duo-install-17.png){: .align-center}

Cada uno de nuestros usuarios recibirá un correo con un enlace único el cual servirá para registrar el usuario y activar la aplicación para la autenticación

![duo-install-18]({{ site.imagesposts2021 }}/03/duo-install-18.png){: .align-center}


# Desplegar aplicación View

## Configurar Connection Server

# Test



