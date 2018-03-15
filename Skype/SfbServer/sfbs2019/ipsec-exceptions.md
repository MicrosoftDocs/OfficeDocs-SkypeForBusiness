---
title: "IPsec exceptions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 241f1eca-6f2f-44de-90b1-2cb659cbe27c
description: "For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation."
---

# IPsec exceptions in Lync Server 2013
[]
For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation.
  
The following table explains the recommended IPsec exception settings. 
  
**Recommended IPsec Exceptions**

|**Rule name**|**Source IP**|**Destination IP**|**Protocol**|**Source port**|**Destination port**|**Authentication Requirement**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|A/V Edge Server Internal Inbound  <br/> |Any  <br/> |A/V Edge Server Internal  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server External Inbound  <br/> |Any  <br/> |A/V Edge Server External  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server Internal Outbound  <br/> |A/V Edge Server Internal  <br/> |Any  <br/> |UDP &amp; TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server External Outbound  <br/> |A/V Edge Server External  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Mediation Server Inbound  <br/> |Any  <br/> |Mediation  <br/> Server(s)  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Mediation Server Outbound  <br/> |Mediation  <br/> Server(s)  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Conferencing Attendant Inbound  <br/> |Any  <br/> |Front End Server running Conferencing Attendant  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Conferencing Attendant Outbound  <br/> |Front End Server running Conferencing Attendant  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Conferencing Inbound  <br/> |Any  <br/> |Front End Servers  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Conferencing Outbound  <br/> |Front End Servers  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Exchange Inbound  <br/> |Any  <br/> |Exchange Unified Messaging  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Application Sharing Servers Inbound  <br/> |Any  <br/> |Application Sharing Servers  <br/> |TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Application Sharing Server Outbound  <br/> |Application Sharing Servers  <br/> |Any  <br/> |TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Exchange Outbound  <br/> |Exchange Unified Messaging  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Clients  <br/> |Any  <br/> |Any  <br/> |UDP  <br/> |Specified media port range  <br/> |Any  <br/> |Do not authenticate  <br/> |
   

