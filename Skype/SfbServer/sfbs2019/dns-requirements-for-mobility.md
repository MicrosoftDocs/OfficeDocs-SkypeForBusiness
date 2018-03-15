---
title: "DNS requirements for mobility with Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df6962bc-2a16-440e-a333-022ebd14f957

description: "When you deploy the Lync Server 2013 mobility feature, you can use the new URLs that are available with the Microsoft Lync Server 2013 Autodiscover Service, or you can use your existing Web Services URLs. If you use your existing URLs, users need to manually enter the URLs in their mobile device settings. This option is typically used for troubleshooting. When you use the new URLs, mobile clients can automatically discover Lync Server 2013 resources. When you support automatic discovery, you need to add new Domain Name System (DNS) records. This section describes the DNS records that are required for automatic discovery."
---

# DNS requirements for mobility with Lync Server 2013
[]
When you deploy the Lync Server 2013 mobility feature, you can use the new URLs that are available with the Microsoft Lync Server 2013 Autodiscover Service, or you can use your existing Web Services URLs. If you use your existing URLs, users need to manually enter the URLs in their mobile device settings. This option is typically used for troubleshooting. When you use the new URLs, mobile clients can automatically discover Lync Server 2013 resources. When you support automatic discovery, you need to add new Domain Name System (DNS) records. This section describes the DNS records that are required for automatic discovery. 
  
To support automatic discovery, you need to create the following DNS records for each SIP domain:
  
- An internal DNS record to support mobile users who connect from within your organization's network
    
- An external, or public, DNS record to support mobile users who connect from the Internet
    
The internal automatic discovery URL should not be addressable from outside your network. The external automatic discovery URL should not be addressable from within your network. However, if you cannot meet this requirement for the external URL, mobile client functionally should not be affected.
  
The DNS records can be either CNAME records or A (host) records.
  
 **Internal DNS records**
  
You need to create one of the following internal DNS records:
  
|**Record type**|**Host name or SRV definition**|**Resolves to**|
|:-----|:-----|:-----|
|CNAME  <br/> |lyncdiscoverinternal. _\<sipdomain\>_ <br/> |Internal Web Services fully qualified domain name (FQDN) for your Director pool, if you have one, or for your Front End pool if you do not have a Director  <br/> |
|A (host)  <br/> |lyncdiscoverinternal. _\<sipdomain\>_ <br/> |Internal Web Services IP address (virtual IP (VIP) address if you use a load balancer) of your Director pool, if you have one, or of your Front End pool if you do not have a Director  <br/> |
   
 **External DNS records**
  
You need to create one of the following external DNS records:
  
|**Record type**|**Host name**|**Resolves to**|
|:-----|:-----|:-----|
|CNAME  <br/> |lyncdiscover.  _\<sipdomain\>_ <br/> |External Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director  <br/> |
|A (host)  <br/> |lyncdiscover.  _\<sipdomain\>_ <br/> |External or public IP address (VIP address if you use a load balancer) of the reverse proxy  <br/> |
|SRV  <br/> |_sipfederationtls._tcp.  _\<sipdomain\>_ <br/> Resolves to host (A or AAAA) record for the Access Edge service  <br/> |To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain that has Microsoft Lync Mobile clients.  <br/> > [!IMPORTANT]> This requirement applies only to Microsoft Lync Mobile clients on Apple or Microsoft based mobile devices. Andriod and Nokia Symbian devices do not use push notification.           |
   
> [!NOTE]
> Lyncdiscover, also known as autodiscover, traffic goes through the reverse proxy. SRV record points to a record that resolves through the Access Edge service. 
  

