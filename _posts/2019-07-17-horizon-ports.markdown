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
|Horizon Client   | *			    |Horizon Agent|3389	   |TCP		   |Microsoft RDP	         |
|Horizon Client   | *			    |Horizon Agent|9427	   |TCP		   |Redirección Windows media MMR	         |
|Horizon Client   | *			    |Horizon Agent|32111   |TCP		   |Redirección USB	         |
|Horizon Client   | *			    |Horizon Agent|4172	   |TCP	y UDP  |PCoIP	         |
|Horizon Client   | *			    |Horizon Agent|22443   |TCP	y UDP  |Blast	         |
|Connection Server y security server| *			    |Horizon Agent|3389	   |TCP 	   |	         |



#	Conexión interna

| Origen    	      |  Destino    			 |Puerto   |Protocolo  |Descripción    		   |
|:-------------------:|:------------------------:|:-------:|:---------:|:---------------------:|
|Horizon Client       |Horizon Connection Server |443	   |TCP		   |Login	       	  	   |
|Horizon Client       |Horizon Agent			 |22443	   |TCP	y UDP  |Blast Extreme     	   |
|Horizon Client       |Horizon Agent			 |4172	   |TCP	y UDP  |PCoIP			  	   |
|Horizon Client       |Horizon Agent			 |3389	   |TCP		   |RDP				  	   |
|Horizon Client       |Horizon Agent			 |9427	   |TCP		   |CDR (client drive redirection)	y MMR (multimedia redirection)		  |
|Horizon Client       |Horizon Agent			 |3211	   |TCP		   |Redirección USB	  	   |
|Navegador Web        |Horizon Agent			 |8443	   |TCP		   |Horizon 7 HTML Access  |



Espero que os sirva.

Un saludo!

Miquel.


