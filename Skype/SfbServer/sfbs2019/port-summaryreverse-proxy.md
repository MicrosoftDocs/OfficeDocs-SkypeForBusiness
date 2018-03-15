---
title: "Port summary - Reverse proxy in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 59b9ac3c-3e6f-4776-b366-174f0dd1f2eb
description: "The reverse proxy has minimal requirements for firewall and port/protocol."
---

# Port summary - Reverse proxy in Lync Server 2013
[]
The reverse proxy has minimal requirements for firewall and port/protocol.
  
- External firewall requirements are the HTTPS/TCP/443 and the optional HTTP/TCP/80. HTTPS is used for SSL and TLS secure communications through the reverse proxy. HTTP is used if you choose to allow access to the Autodiscover Service when modifying certificates might prove difficult or not cost justified.
    
- Clients expect to contact the Office Web Apps Server on HTTPS. The Office Web Apps Server expects communication from internal clients on HTTPS/TCP/443. The recommended configuration is to allow HTTPS/TCP/443 from the reverse proxy to the Office Web Apps Server.
    
- Port 8080 is used to route traffic from the reverse proxy internal interface to the Front End Server, Front End pool virtual IP (VIP) or the optional Director or Director pool VIP. Port TCP 8080 is required for mobile devices running Lync to locate the Autodiscover Service in situations where modifying the external web service publishing rule certificate is undesirable (for example, if you have a large number of SIP domains). If you choose to acquire new certificates with the necessary SAN entries, the port TCP 8080 is not needed and is optional.
    
- Port 4443 is used for traffic from the reverse proxy internal interface to the Front End Server, Front End pool virtual IP (VIP) or the optional Director or Director pool VIP
    
     ![Reverse Proxy and External Web Services](media/Plan_LyncServer_Edge_RP_Reverse_Proxy_Common.jpg)
  
    > [!CAUTION]
    > Do not confuse the 4443 over TCP from the reverse proxy to the internal deployment for the port 4443 over TCP traffic from the Standard Edition server or the Front End pool that manages the Central Management store role. 
  
## Port and Protocol Details

**Firewall Details for Reverse Proxy Server: External Interface**

|**Protocol/TCP or UDP/Port**|**Source IP Address**|**Destination IP Address**|**Notes**|
|:-----|:-----|:-----|:-----|
|HTTP/TCP/80  <br/> |Any  <br/> |Reverse proxy listener  <br/> |(Optional) Redirection to HTTPS if user enters http:// _\<publishedSiteFQDN\>_.  <br/> Also required if using Office Web Apps for conferencing and the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate.  <br/> |
|HTTPS/TCP/443  <br/> |Any  <br/> |Reverse proxy listener  <br/> |Address book downloads, Address Book Web Query service, Autodiscover, client updates, meeting content, device updates, group expansion, Office Web Apps for conferencing, dial-in conferencing, and meetings.  <br/> |
   
**Firewall Details for Reverse Proxy Server: Internal Interface**

|**Protocol/TCP or UDP/Port**|**Source IP Address**|**Destination IP Address**|**Notes**|
|:-----|:-----|:-----|:-----|
|HTTP/TCP/8080  <br/> |Internal reverse proxy interface  <br/> |Front End Server, Front End pool, Director, Director pool  <br/> |Required if using the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate.  <br/> Traffic sent to port 80 on the reverse proxy external interface is redirected to a pool on port 8080 from the reverse proxy internal interface so that the pool Web Services can distinguish it from internal web traffic.  <br/> |
|HTTPS/TCP/4443  <br/> |Internal reverse proxy interface  <br/> |Front End Server, Front End pool, Director, Director pool  <br/> |Traffic sent to port 443 on the reverse proxy external interface is redirected to a pool on port 4443 from the reverse proxy internal interface so that the pool web services can distinguish it from internal web traffic.  <br/> |
|HTTPS/TCP/443  <br/> |Internal reverse proxy interface  <br/> |Office Web Apps for conferencing  <br/> ||
   

