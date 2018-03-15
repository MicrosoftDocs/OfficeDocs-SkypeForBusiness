---
title: "Port summary - Autodiscover in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 4/6/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8bd16363-5e18-4e4b-be99-b3e6457b4c99

description: "The Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS using the lyncdiscover.<domain> and lyncdiscoverinternal.<domain> host records, can be used by clients to locate Lync Server features. In order for mobile devices running Lync Mobile to use Autodiscover, you may first need to modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies."
---

# Port summary - Autodiscover in Lync Server 2013
[]
The Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS using the  `lyncdiscover.<domain>` and  `lyncdiscoverinternal.<domain>` host records, can be used by clients to locate Lync Server features. In order for mobile devices running Lync Mobile to use Autodiscover, you may first need to modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies. 
  
The decision about whether to use subject alternative name lists on reverse proxies is based on whether you publish the Autodiscover Service on port 80 or on port 443:
  
- **Published on port 80** For Mobile devices, no certificate changes are required if the initial query to the Autodiscover Service occurs over port 80. This is because mobile devices running Lync will access the reverse proxy on port 80 externally and then be redirected to a Director or Front End Server on port 8080 internally. 
    
- **Published on port 443** The subject alternative name list on certificates used by the external web services publishing rule must contain a  `lyncdiscover.<sipdomain>` entry for each SIP domain within your organization. 
    
    > [!IMPORTANT]
    > For new installations or upgrades from Lync Server 2010 where you deployed Mobility, you either used Port 80 for Autodiscover of the Mobility service, or reissued certificates with the proper subject name and subject alternative names in place. Review the certificates on your Director and Front End Server to confirm which path you chose. 
  
**Firewall Details for Reverse Proxy Server: External Interface**

|**Protocol/TCP or UDP/Port**|**Source IP Address**|**Destination IP Address**|**Notes**|
|:-----|:-----|:-----|:-----|
|HTTP/TCP/80  <br/> |Any  <br/> |Reverse proxy listener  <br/> |(Optional) Redirection to HTTPS if user enters http:// _\<publishedSiteFQDN\>_. Also required if using Office Web Apps for conferencing and the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate.  <br/> |
|HTTPS/TCP/443  <br/> |Any  <br/> |Reverse proxy listener  <br/> |Address book downloads, Address Book Web Query service, Autodiscover, client updates, meeting content, device updates, group expansion, Office Web Apps for conferencing, dial-in conferencing, and meetings.  <br/> |
   
**Firewall Details for Reverse Proxy Server: Internal Interface**

|**Protocol/TCP or UDP/Port**|**Source IP Address**|**Destination IP Address**|**Notes**|
|:-----|:-----|:-----|:-----|
|HTTP/TCP/8080  <br/> |Internal reverse proxy interface  <br/> |Front End Server, Front End pool, Director, Director pool, Office Web Apps for conferencing  <br/> |Required if using the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate. Traffic sent to port 80 on the reverse proxy external interface is redirected to a pool on port 8080 from the reverse proxy internal interface so that the pool Web Services can distinguish it from internal web traffic.  <br/> |
|HTTPS/TCP/4443  <br/> |Internal reverse proxy interface  <br/> |Front End Server, Front End pool, Director, Director pool, Office Web Apps for conferencing  <br/> |Traffic sent to port 443 on the reverse proxy external interface is redirected to a pool on port 4443 from the reverse proxy internal interface so that the pool web services can distinguish it from internal web traffic.  <br/> > [!NOTE]> If you employ network-level or machine-level firewalls between pools, port 4443 will need to be opened for Inter-Pool Front End to Front end referrals.           |
   

