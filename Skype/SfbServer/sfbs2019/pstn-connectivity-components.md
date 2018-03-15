---
title: "PSTN connectivity components in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6b2a3f7d-760f-4f09-8432-312c98a7e6b7
description: "In this articleSIP TrunkingPSTN gatewaysPrivate Branch Exchanges"
---

# PSTN connectivity components in Lync Server 2013
[]
 **In this article**
  
[SIP Trunking](#sectionSection0)
  
[PSTN gateways](#sectionSection1)
  
[Private Branch Exchanges](#sectionSection2)
  
An enterprise-grade VoIP solution must provide for calls to and from the public switched telephone network (PSTN) without any decline in Quality of Service (QoS). In addition, users should not be aware of the underlying technology when they place and receive calls. From the user's perspective, a call between the Enterprise Voice infrastructure and the PSTN should seem like just another SIP session.
  
For PSTN connections, you can either deploy a SIP trunk or a PSTN gateway (with a PBX, also known as a Direct SIP link, or without a PBX).
  
## SIP Trunking
<a name="sectionSection0"> </a>

As an alternative to using PSTN gateways, you can connect your Enterprise Voice solution to the PSTN by using SIP trunking. SIP trunking enables the following scenarios:
  
- An enterprise user inside or outside the corporate firewall can make a local or long-distance call specified by an E.164-compliant number that is terminated on the PSTN as a service of the corresponding service provider.
    
- Any PSTN subscriber can contact an enterprise user inside or outside the corporate firewall by dialing a Direct Inward Dialing (DID) number associated with that enterprise user.
    
The use of this deployment solution requires a SIP trunking service provider. 
  
## PSTN gateways
<a name="sectionSection1"> </a>

PSTN gateways are third-party devices that translate signaling and media between the Enterprise Voice infrastructure and a PSTN or a PBX. PSTN gateways work with the Mediation Server to present a PSTN or PBX call to an Enterprise Voice client. The Mediation Server also presents calls from Enterprise Voice clients to the PSTN gateway for routing to the PSTN or PBX. For a list of partners who work with Microsoft to provide devices that work with Lync Server, see the Microsoft Unified Communications Partners website at [https://go.microsoft.com/fwlink/p/?linkId=202836](https://go.microsoft.com/fwlink/p/?linkId=202836). 
  
## Private Branch Exchanges
<a name="sectionSection2"> </a>

 If you have an existing voice infrastructure that uses a private branch exchange (PBX), you can use your PBX with Lync Server Enterprise Voice. 
  
The supported Enterprise Voice-PBX integration scenarios are as follows:
  
- IP-PBX that supports media bypass, with a Mediation Server.
    
- IP-PBX that requires a stand-alone PSTN gateway.
    
- Time division multiplexing (TDM) PBX, with a stand-alone PSTN gateway.
    
> [!NOTE]
> Media bypass will not interoperate with every PSTN gateway, IP-PBX, and SBC. Microsoft has tested a set of PSTN gateways and SBCs with certified partners and has done some testing with Cisco IP-PBXs. Media bypass is supported only with products and versions listed on Unified Communications Open Interoperability Program - Lync Server at [https://go.microsoft.com/fwlink/p/?linkId=214406](https://go.microsoft.com/fwlink/p/?linkId=214406). 
  
For details about partners who offer Enterprise Voice solutions, see the Microsoft Unified Communications Partners website at [https://go.microsoft.com/fwlink/p/?linkId=202836](https://go.microsoft.com/fwlink/p/?linkId=202836).
  
For details about partners who offer Enterprise Voice hardware solutions, including PSTN gateways, see the Microsoft Unified Communications Partners website [https://go.microsoft.com/fwlink/p/?linkId=202836](https://go.microsoft.com/fwlink/p/?linkId=202836).
  

