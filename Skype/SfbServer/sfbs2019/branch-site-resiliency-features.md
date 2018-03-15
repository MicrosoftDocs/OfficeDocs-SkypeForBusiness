---
title: "Branch-site resiliency features in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8e3feda5-9a38-4e3c-b808-af29f19c5eb9
description: "If you provide branch-site resiliency, if a branch site's WAN connection to a central site fails or if the central site is unreachable, the following voice features should continue to be available:"
---

# Branch-site resiliency features in Lync Server 2013
[]
If you provide branch-site resiliency, if a branch site's WAN connection to a central site fails or if the central site is unreachable, the following voice features should continue to be available:
  
## 

- Inbound and outbound public switched telephone network (PSTN) calls
    
- Enterprise calls between users at both the same site and between two different sites
    
- Basic call handling, including call hold, retrieval, and transfer
    
- Two-party instant messaging
    
- Call forwarding, simultaneous ringing of endpoints, call delegation, and team call services, but only if the delegator and delegate (for example, a manager and the manager's administrator), or all team members, are configured at the same site
    
- Call detail records (CDRs)
    
- PSTN dial-in conferencing with Conferencing Auto-Attendant
    
- Voice mail capabilities, if you configure voice mail rerouting settings. (For details, see [Branch-site resiliency requirements for Lync Server 2013](branch-site-resiliency-requirements.md).)
    
- User authentication and authorization
    
The following features will be available only if your resiliency solution is a full-scale Lync Server deployment at the branch site:
  
- IM, web, and A/V conferencing
    
- Presence and Do Not Disturb (DND)-based routing (where calls are prevented from ringing on extensions that have DND activated)
    
- Updating call forwarding settings
    
- Response Group application and Call Park application
    
- Provisioning new phones and clients, but only if Active Directory Domain Services is present at the branch site.
    
- Enhanced 9-1-1 (E9-1-1)
    
    If E9-1-1 is deployed, and the SIP trunk at the central site is not available because the WAN link is down, then the Survivable Branch Appliance will route E9-1-1 calls to the local branch gateway. To enable this feature, the branch-site users' voice policies should route calls to the local gateway in the event of WAN failure.
    
> [!NOTE]
> SBA (survivable branch office) is not supported for XMPP. Users homed in a SBA configurations will not be able to send IMs or see Presence with XMPP contacts. 
  

