---
title: "Plan for Edge Server certificates in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f1dfe220-2398-4ac8-ba4c-206c8c0cbc50
description: "Certificate creation for Edge is simplified in Lync Server 2013."
---

# Plan for Edge Server certificates in Lync Server 2013
[]
Certificate creation for Edge is simplified in Lync Server 2013.
  
**Certificates Flow Chart for Edge Server**

![Certificates Flow Chart](media/Plan_LyncServer_Edge_Scenario_EdgeServerOnlyCertificateFlowchart.jpg)
  
Create a single public certificate, ensure that you have an exportable private key defined for the certificate, and assign it to the following Edge Server external interfaces using the certificate wizard:
  
> [!IMPORTANT]
> Wildcard certificates are not supported in Lync Server, except where used to summarize the Simple URLs through the reverse proxy. You must define distinct subject alternate names (SANs) for each SIP domain name, Web Conferencing Edge service, A/V Edge service and XMPP domain offered by your deployment. 
  
> [!NOTE]
> Introduced in Lync Server 2013, staging Audio/Video Authentication certificates in advance of the expiration time of the current certificate requires some additional planning. Instead of one certificate with multiple purposes for the external Edge interface, you will require two certificates, one assigned to the Access Edge service and Web Conferencing Edge service, and one certificate for the A/V Edge service. For additional details, see [Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate](staging-av-and-oauth-certificates-using-roll-in-set-cscertificate.md)
  
> [!IMPORTANT]
> In the event of a pool of Edge Servers, you export the certificate with the private key to each Edge Server and assign the certificate to each Edge Server service. Do the same for the internal Edge Server certificate, exporting the certificate with the private key and assigning to each internal Edge interface. 
  
- Ensure that you have an exportable private key assigned for the certificate
    
- Access Edge service (referred to as **SIP Access Edge External** in the certificate wizard) 
    
- Web Conferencing Edge service (referred to as **Web Conferencing Edge External** in the certificate wizard) 
    
- A/V Authentication service (referred to as **A/V Edge External** in the certificate wizard) 
    
Create a single internal certificate with exportable private key, copy and assign it to each of the Edge Server internal interfaces:
  
- Edge Server (referred to as **Edge Internal** in the certificate wizard) 
    
> [!IMPORTANT]
> It is possible to use separate and distinct certificates for each Edge Server service. A good reason to choose separate certificates is if you want to use the new rolling certificate feature for the A/V Edge service certificate. In the case of this feature, decoupling the A/V Edge service certificate from the Access Edge service and Web Conferencing Edge service is recommended. If you choose to request, acquire and assign separate certificates for each service, you must request that the private key be exportable for the A/V Edge service (again, this is in actuality the A/V Authentication service) and assign the same certificate to the A/V Edge External interface on each Edge Server. 
  
## See also

#### 

[Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate](staging-av-and-oauth-certificates-using-roll-in-set-cscertificate.md)
#### 

[Changes in Lync Server 2013 that affect Edge Server planning](changes-in-lync-server-2013-that-affect-edge-server-planning.md)

