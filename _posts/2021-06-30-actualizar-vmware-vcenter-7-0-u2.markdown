---
title: Actualizar nuestro VMware vCenter a la última versión 7.0U2b
date: '2021-06-30 00:00:00'
layout: post
image: /assets/images/posts/2018/12/ssh-banner.jpg
tag:
- vmware
- vexpert
- vcenter
---

Buenos dias a todos. En el post de hoy veremos cómo actualizar nuestro vCenter a la última versión disponible. La 7.0 U2b

# Actualizar nuestro VMware vCenter a la última versión 7.0U2b

Lo primero quen haremos será descargar la iso correspondiente a la última versión desde el portal de [my.vmware](my.vmware.com)

![update-vcenter-00]({{ site.imagesposts2021 }}/06/update-vcenter-00.png){: .align-center}

Con la iso ya descargada, arrancaremos el asistente de actualización y seguiremos el asistente

![update-vcenter-01]({{ site.imagesposts2021 }}/06/update-vcenter-01.png){: .align-center}

![update-vcenter-02]({{ site.imagesposts2021 }}/06/update-vcenter-02.png){: .align-center}

Aceptamos los terminos de licencia

![update-vcenter-03]({{ site.imagesposts2021 }}/06/update-vcenter-03.png){: .align-center}

Completamos los datos de conexión tanto de nuestro vCenter cómo del ESXi en el que corre la VM.

![update-vcenter-04]({{ site.imagesposts2021 }}/06/update-vcenter-04.png){: .align-center}

Aceptamos el certificado autofirmado de conexión

![update-vcenter-05]({{ site.imagesposts2021 }}/06/update-vcenter-05.png){: .align-center}

Indicaremos los datos del ESXi en dónde se desplegará el nuevo appliance

![update-vcenter-06]({{ site.imagesposts2021 }}/06/update-vcenter-06.png){: .align-center}

Aceptaremos de nuevo el certificado, esta vez del ESXi

![update-vcenter-07]({{ site.imagesposts2021 }}/06/update-vcenter-07.png){: .align-center}

Definimos el nombre que tendrá la VM en el inventario

![update-vcenter-08]({{ site.imagesposts2021 }}/06/update-vcenter-08.png){: .align-center}

Definimos el tamaño del appliance

![update-vcenter-09]({{ site.imagesposts2021 }}/06/update-vcenter-09.png){: .align-center}

Definimos la LUN en dónde se almacenará la VM y marcamos el check de Thin Provisioning

![update-vcenter-10]({{ site.imagesposts2021 }}/06/update-vcenter-10.png){: .align-center}

Definiremos la configuración de red que tendrá nuestra nueva VM, definiremos una IP temporal que se usará durante el proceso de migración

![update-vcenter-11]({{ site.imagesposts2021 }}/06/update-vcenter-11.png){: .align-center}

Comprobaremos que los datos introducidos son correctos y "Finish"

![update-vcenter-12]({{ site.imagesposts2021 }}/06/update-vcenter-12.png){: .align-center}

Vemos cómo se lanza el proceso de Deploy y cómo aparece la nueva VM en el inventario del vCenter

![update-vcenter-13]({{ site.imagesposts2021 }}/06/update-vcenter-13.png){: .align-center}

