---
title: "DNS summary - Single Director in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 790ecb56-92cd-41f4-baf6-c290a707aa4d
description: "The following table contains a summary of the DNS records that are required to support the single Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director does not host user accounts or host the Mobility Services."
---

# DNS summary - Single Director in Lync Server 2013
[]
The following table contains a summary of the DNS records that are required to support the single Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director does not host user accounts or host the Mobility Services.
  
**DNS Records Required for the Director**

|**Location/TYPE/Port**|**FQDN/DNS Record**|**IP Address/FQDN**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|Internal DNS/A  <br/> |dir01.contoso.net  <br/> |Director  <br/> |Director host record used for replication and server to server  <br/> |
|Internal DNS/A  <br/> |sip.contoso.com  <br/> |Director  <br/> |Inbound session initiation protocol (SIP) from the internal Edge interface of the Edge Server  <br/> |
|Internal DNS/A  <br/> |dialin.contoso.com  <br/> |Director  <br/> |Published dialin web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |meet.contoso.com  <br/> |Director  <br/> |Published meet web services from reverse proxy  <br/> |
|Internal DNS/A  <br/> |webdirexternal.contoso.com  <br/> |Director  <br/> |Published and defined by the reverse proxy Web Ticket external web services for the Director  <br/> |
   

