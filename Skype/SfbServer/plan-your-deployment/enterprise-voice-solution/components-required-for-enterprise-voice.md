---
title: "Components required for Enterprise Voice in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: ee219976-c39a-4b2f-988d-886c339700f7
description: "A summary of the Enterprise Voice components in Skype for Business Server."
---

# Components required for Enterprise Voice in Skype for Business Server
 
A summary of the Enterprise Voice components in Skype for Business Server.
  
To deploy Enterprise Voice, the following components are required in your topology. 
  
- One or more Mediation Servers, which translate signaling and, in some configurations, media between your internal Skype for Business Server, Enterprise Voice infrastructure and a public switched telephone network (PSTN) gateway or a Session Initiation Protocol (SIP) trunk. The Mediation Servers are the most crucial component in your Enterprise Voice deployment. For more information, see [Mediation Server component in Skype for Business Server](mediation-server.md).
    
    Mediation Servers can be collocated with Front End Servers or installed as standalone servers.
    
- PSTN connectivity components, which can include SIP trunks or PSTN gateways. For more information, see [PSTN connectivity components in Skype for Business Server](pstn-connectivity.md).
    
- Edge Servers, which enables the use of Enterprise Voice features by your users when they are outside your organization's firewall. 
    
    The Access Edge service provides SIP signaling for calls from Skype for Business users who are outside your organization's firewall. The A/V Edge service enables media traversal of NAT and firewalls. A caller who uses a unified communications (UC) client from outside the corporate firewall relies on the A/V Edge service for both individual and conference calls.
    
    The A/V Authentication service is collocated with, and provides authentication services for, the A/V Edge service. Outside users who attempt to connect to the A/V Edge service require an authentication token that is provided by the A/V Authentication Service before their calls can go through.
    
- Additionally, some Enterprise Voice components run on Front End Servers. For details about these components, see [Front End Server VoIP components for Skype for Business Server](front-end-server-voip.md)
    

