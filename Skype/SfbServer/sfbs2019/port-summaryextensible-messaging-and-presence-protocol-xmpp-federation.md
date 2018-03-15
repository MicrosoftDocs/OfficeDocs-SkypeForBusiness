---
title: "Port summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 62e98fab-7add-4983-a3fa-dbe74e1c3849
description: "The ports and protocols defined for the extensible messaging and presence protocol (XMPP) proxy deployed on the Edge Server allow communications from the XMPP federated partner to the Edge Server, and also allows communication from your Edge Server to the XMPP federated partner. A rule is also defined on the internal-facing firewall from the Front End Server or Front End pool to the Edge Server or Edge pool."
---

# Port summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013
[]
The ports and protocols defined for the extensible messaging and presence protocol (XMPP) proxy deployed on the Edge Server allow communications from the XMPP federated partner to the Edge Server, and also allows communication from your Edge Server to the XMPP federated partner. A rule is also defined on the internal-facing firewall from the Front End Server or Front End pool to the Edge Server or Edge pool. 
  
## Firewall Summary for Extensible Messaging and Presence Protocol

|**Protocol/TCP or UDP/Port**|**Source (IP address)**|**Destination (IP address)**|**Comments**|
|:-----|:-----|:-----|:-----|
|XMPP/TCP/5269  <br/> | Any  <br/> |Access Edge service interface IP address  <br/> |Standard server-to-server communication port for XMPP. Allows communication to the Edge Server XMPP proxy from federated XMPP partners  <br/> |
|XMPP/TCP/5269  <br/> |Access Edge service interface IP address  <br/> |Any  <br/> |Standard server-to-server communication port for XMPP. Allows communication from the Edge Server XMPP proxy to federated XMPP partners  <br/> |
|XMPP/MTLS/23456  <br/> |Any  <br/> |Internal Edge Server Interface IP  <br/> |Internal XMPP traffic from the XMPP Gateway on the Front End Server or Front End pool to the Edge Server  <br/> |
   
## See also

#### 

[Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk](example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)
#### 

[Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md)

