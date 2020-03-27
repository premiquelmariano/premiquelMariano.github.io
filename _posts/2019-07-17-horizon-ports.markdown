---
title: Puertos TCP y UDP utilizados por Horizon 7
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
permalink: /ports/

---

Buenos dias a tod@s!!

#	Horizon Agent y Horizon Client

| Origen          | Puerto          | Destino     |Puerto  |Protocolo  |Descripción  |
| :--------------:|:---------------:| :----------:|:------:|:---------:|:-----------:|
|Horizon Client   | *			    |Horizon Agent|3389	   |TCP		   |	         |
|Horizon Client   | *			    |Horizon Agent|9427	   |TCP		   |	         |
|Horizon Client   | *			    |Horizon Agent|32111   |TCP		   |	         |
|Horizon Client   | *			    |Horizon Agent|4172	   |TCP	y UDP  |	         |
|Horizon Client   | *			    |Horizon Agent|22443   |TCP	y UDP  |	         |
|Connection Server y security server| *			    |Horizon Agent|3389	   |TCP 	   |	         |



#	Conexión interna

Espero que os sirva.

Un saludo!

Miquel.


