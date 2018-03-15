---
title: "DNS summary - DNS and HLB load balanced in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d2132695-1956-4190-a98e-cd7255cbded6
description: "The following table contains a summary of the DNS records that are required to support the DNS load balanced and hardware load balanced Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director pool does not host user accounts or host the Mobility Services."
---

# DNS summary - DNS and HLB load balanced in Lync Server 2013
[]
The following table contains a summary of the DNS records that are required to support the DNS load balanced and hardware load balanced Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director pool does not host user accounts or host the Mobility Services.
  
**DNS Records Required for the Director Pool using DNS Load Balancing and Hardware Load Balancer**

|**Location/TYPE/Port**|**FQDN/DNS Record**|**IP Address/FQDN**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|Internal DNS/A  <br/> |dir01.contoso.net  <br/> |Director  <br/> |Director host record used for replication and server to server  <br/> |
|Internal DNS/A  <br/> |dirpool01.contoso.net  <br/> |Director pool  <br/> |Host record for the DNS load balanced Director pool for server to server  <br/> |
|Internal DNS/A  <br/> |sip.contoso.com  <br/> |Director pool  <br/> |Inbound session initiation protocol (SIP) from the internal interface of the Edge Server  <br/> |
|Internal DNS/A  <br/> |dialin.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published dialin web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |meet.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published meet web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |webdirexternal.contoso.com  <br/> |Director pool HLB VIP  <br/> |Hardware load balanced published and defined by the reverse proxy Web Ticket external web services for the Director pool  <br/> |
   

