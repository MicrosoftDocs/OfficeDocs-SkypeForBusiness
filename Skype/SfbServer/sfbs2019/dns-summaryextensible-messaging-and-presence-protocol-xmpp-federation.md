---
title: "DNS summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f720a2a-8ab5-43cc-882a-ab595ed3cec7
description: "To configure extensible messaging and presence protocol (XMPP) for your deployment, you create two Domain Name System (DNS) records in an external DNS server that will resolve the records to the Access Edge service of your Edge Server or Edge pool."
---

# DNS summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013
[]
To configure extensible messaging and presence protocol (XMPP) for your deployment, you create two Domain Name System (DNS) records in an external DNS server that will resolve the records to the Access Edge service of your Edge Server or Edge pool.
  
## DNS Summary for Extensible Messaging and Presence Protocol

|**Location/TYPE/Port**|**FQDN**|**IP address/FQDN host record**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|External DNS/SRV/5269  <br/> |_xmpp-server._tcp.contoso.com  <br/> |xmpp.contoso.com  <br/> |XMPP proxy external interface on the Access Edge service or Edge pool.Repeat as necessary for all internal SIP domains with Lync enabled users where contact with XMPP contacts is allowed through the configuration of the External Access Policy through a global policy, site policy where the user is located, or user policy applied to the Lync-enabled user. An allowed XMPP domain must also be configured in the XMPP Federated Partners policy. See topics in **See Also** for additional details  <br/> |
|External DNS/A  <br/> |xmpp.contoso.com (for example)  <br/> |IP address of Access Edge service on your Edge Server or Edge pool hosting XMPP proxy  <br/> |Points to the Access Edge service or Edge pool that hosts the XMPP proxy service. Typically, the SRV record that you create will point to this host (A or AAAA) record  <br/> |
   
## See also

#### 

[Setting up XMPP federation in Lync Server 2013](setting-up-xmpp-federation.md)
#### 

[Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md)

