---
title: "Port summary - Public instant messaging connectivity in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f46756ec-1401-4ca2-a4a4-5cd28bcfdc7f
description: "To configure your firewall for ports and protocols necessary to support public instant messaging connectivity, first note that SIP/MTLS/TCP 5061 is bidirectional to account for the ability of contacts in the public IM provider to contact Lync clients, or for Lync to contact public IM contacts."
---

# Port summary - Public instant messaging connectivity in Lync Server 2013
[]
To configure your firewall for ports and protocols necessary to support public instant messaging connectivity, first note that SIP/MTLS/TCP 5061 is bidirectional to account for the ability of contacts in the public IM provider to contact Lync clients, or for Lync to contact public IM contacts.
  
Windows Live Messenger can participate in audio/video communications with Lync clients. This accounts for the very similar firewall port and protocol configuration that you would typically have on the firewall to support Lync clients as external users.
  
> [!IMPORTANT]
> More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard Client Access License (CAL). Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice. > Federation with Messenger client contacts will officially end on March 15, 2013, except for mainland China. Skype will become the federation client for federated users who previously used Messenger. 
  
## Firewall Summary - Public Instant Messaging Connectivity

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Public IM connectivity partners  <br/> |Edge Server Access interface  <br/> |For federated and public IM connectivity that use SIP.  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Edge Server Access interface  <br/> |Public IM connectivity partners  <br/> |For federated and public IM connectivity that use SIP.  <br/> |
|Access/SIP(TLS)/TCP/443  <br/> |Clients  <br/> |Edge Server Access interface  <br/> |Client-to-server SIP traffic for external user access.  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Edge Server Access interface  <br/> |Live Messenger clients  <br/> |Used for A/V sessions with Windows Live Messenger if public IM connectivity is configured.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Edge Server Access interface  <br/> |Live Messenger clients  <br/> |Required for public IM connectivity with Windows Live Messenger.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Live Messenger clients  <br/> |Edge Server Access interface  <br/> |Required for public IM connectivity with Windows Live Messenger.  <br/> |
   
## See also

#### 

[Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)
  
[Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md)

