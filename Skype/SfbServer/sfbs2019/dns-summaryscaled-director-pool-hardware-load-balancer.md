---
title: "DNS summary - Scaled Director pool, hardware load balancer in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 08ba48e6-bfa1-4ab0-bc89-d58ddb9c20af
description: "The following table contains a summary of the DNS records that are required to support the hardware load balanced Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director pool does not host user accounts or host the Mobility Services."
---

# DNS summary - Scaled Director pool, hardware load balancer in Lync Server 2013
[]
The following table contains a summary of the DNS records that are required to support the hardware load balanced Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director pool does not host user accounts or host the Mobility Services.
  
**DNS Records Required for the Director pool using a Hardware Load Balancer and DNS Load Balancing**

|**Location/TYPE/Port**|**FQDN/DNS Record**|**IP Address/FQDN**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|Internal DNS/A  <br/> |dir01.contoso.net  <br/> |Director  <br/> |Director host record used for replication and server to server communication  <br/> |
|Internal DNS/A  <br/> |dirpool01.contoso.net  <br/> |Director pool pool HLB VIP  <br/> |Host record for the DNS load balanced Director pool  <br/> |
|Internal DNS/A  <br/> |sip.contoso.com  <br/> |Director pool HLB VIP  <br/> |Inbound session initiation protocol (SIP) from the internal interface of the Edge Server  <br/> |
|Internal DNS/A  <br/> |dialin.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published dialin web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |meet.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published meet web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |webdirexternal.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published and defined by the reverse proxy Web Ticket external web services for the Director pool  <br/> |
   

