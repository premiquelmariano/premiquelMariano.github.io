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

#	Conexión externa

| Origen    	      |  Destino    			 |Puerto   |Protocolo  |Descripción    		   |
|:-------------------:|:------------------------:|:-------:|:---------:|:---------------------:|
|Horizon Client       |UAG o Security server	 |443	   |TCP		   |Login	       	  	   |
|Horizon Client       |UAG o Security server	 |8443	   |TCP	y UDP  |Blast Extreme     	   |
|Horizon Client       |UAG o Security server	 |4172	   |TCP	y UDP  |PCoIP			  	   |
|Horizon Client       |Horizon Agent			 |3389	   |TCP		   |RDP				  	   |
|Horizon Client       |Horizon Agent			 |9427	   |TCP		   |CDR (client drive redirection)	y MMR (multimedia redirection)		  |
|Horizon Client       |Horizon Agent			 |3211	   |TCP		   |Redirección USB	  	   |
|Navegador Web        |Horizon Agent			 |8443	   |TCP		   |Horizon 7 HTML Access  |

#	Horizon Connection Server

| Origen    		      |  Destino    			 |Puerto   |Protocolo  |Descripción    		   |
|:-----------------------:|:------------------------:|:-------:|:---------:|:---------------------:|
|Horizon Connection Server|Horizon Agent			 |22443	   |TCP	y UDP  |Blast Extreme     	   |
|Horizon Connection Server|Horizon Agent			 |4172	   |TCP	y UDP  |PCoIP			  	   |
|Horizon Connection Server|Horizon Agent			 |3389	   |TCP		   |RDP				  	   |
|Horizon Connection Server|Horizon Agent			 |9427	   |TCP		   |CDR (client drive redirection)	y MMR (multimedia redirection)		  |
|Horizon Connection Server|Horizon Agent			 |3211	   |TCP		   |Redirección USB	  	   |
|Horizon Connection Server|Horizon Agent			 |8443	   |TCP		   |Horizon 7 HTML Access  |
|Horizon Connection Server|vCenter Server			 |443	   |TCP		   |SOAP				   |
|Horizon Connection Server|BBDD (eventos)			 |1443	   |TCP		   |Microsoft SQL Server   |
|Horizon Connection Server|BBDD (eventos)			 |1521	   |TCP		   |Oracle server 		   |
|Horizon Connection Server|JMP server 				 |443	   |TCP		   |					   |
|Horizon Connection Server|View Composer			 |18443	   |TCP		   |SOAP				   |






Espero que os sirva.

Un saludo!

Miquel.


