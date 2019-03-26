---
title: Backup de la configuración en Brocade FC Switches [Part 2]
date: '2017-09-22 00:00:00'
layout: post
image: /assets/images/posts/2017/10/brocade-logo.png
headerImage: true
tag:
- backup
- brocade
- fabric
- san
- fc
category: blog
author: miquelMariano
description: Backup de la configuración en Brocade FC Switches [Part 2]
hidden: false
permalink: /backupbrocadeauto/
---

http://systemadmin.es/2009/04/backup-de-la-configuracion-de-la-san-switch-brocade

Buenos días a tod@s!!!

![brocade1]({{ site.imagesposts2019 }}/04/brocade1.png)
![brocade2]({{ site.imagesposts2019 }}/04/brocade2.png)

```ssh
#!/usr/bin/expect

#USAGE
#[root@xorux tmp]# ./backup_san_brocade.sh admin password 10.245.58.19 root xorux4you 10.245.56.195 /tmp/

set swuser [lindex $argv 0]
set swpasswd [lindex $argv 1]
set swhost [lindex $argv 2]

set dstuser [lindex $argv 3]
set dstpasswd [lindex $argv 4]
set dsthost [lindex $argv 5]

set dstfile [lindex $argv 6]

#set file "$(date --date='-1 days' +%Y%m%d_$swhost.txt)"
set DATE [exec date "+%Y%m%d"]
set file $dstfile$swhost-$DATE.txt

spawn ssh -l $swuser $swhost
expect "password:"
send "$swpasswd\r"
expect "to proceed."
send "\003" #To send a "Ctrl-C" in Expect using its octal value, use the command "send \003" in your script.
expect ">"
send "configupload\r"
expect ": "
send "scp\r"
expect ": "
send "N\r"
expect ": "
send "$dsthost\r"
expect ": "
send "$dstuser\r"
expect ": "
send "$file\r"
expect ": "
send "all\r"
expect "password:"
send "$dstpasswd\r"
expect ">"
send "exit\r"
expect eof
```


Espero que os sea de utilidad.
Gracias por compartir

Un saludo

Miquel.





