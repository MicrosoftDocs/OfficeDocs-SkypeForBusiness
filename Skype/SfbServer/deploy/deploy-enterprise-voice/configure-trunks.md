---
title: "Configure trunks in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: a1309c09-ad9a-4c54-9650-4e3f5b2a4a00
description: "Summary: Learn how to configure a trunk between a Mediation Server and peers for Enterprise Voice in Skype for Business Server."
---

# Configure trunks in Skype for Business Server
 
**Summary:** Learn how to configure a trunk between a Mediation Server and peers for Enterprise Voice in Skype for Business Server.
  
As part of Enterprise Voice deployment, you can configure a trunk between a Mediation Server and one or more of the following peers to provide public switched telephone network (PSTN) connectivity for Enterprise Voice clients and devices in your organization:
  
- SIP trunk connection to an Internet telephony service provider (ITSP)
    
- PSTN gateway
    
- Private branch exchange (PBX)
    
For more details, see [Plan for PSTN connectivity in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/pstn-connectivity-0.md).
  
Skype for Business Server functionality supports multiple associations between gateways and Mediation Servers. These associations are made by defining a trunk, which is a logical association between a Mediation Server pool and a public switched telephone network (PSTN) gateway, Session Border Controller (SBC), or IP-PBX. Use the Topology Builder to associate gateways with Mediation Servers (that is, trunks).
  
- To assign or remove a trunk in Skype for Business Server, you must first define a trunk in Topology Builder. A trunk consists of the following association: Mediation Server fully qualified domain name (FQDN), the Mediation Server listening port, the gateway FQDN, and the gateway listening port.
    
- To configure multiple trunks, you can create multiple associations between the same gateway and the Mediation Server. This provides additional resiliency to the Enterprise Voice infrastructure, which is especially useful in private branch exchange (PBX) interoperational scenarios. 
    
When a trunk is defined, it must be associated to a route. To associate a trunk to a route, you define a simple name for the trunk in Topology Builder. This simple name is used as the trunk name in the Skype for Business Server Control Panel, where trunks can be associated with routes. The simple trunk name is used as the gateway name from the Skype for Business Server Management Shell. 
  
```
New-CsVoiceRoute -Identity <RouteId> -NumberPattern <String> -PstnUsages @{add="<UsageString>"} -PstnGatewayList @{add="<TrunkSimpleName>"}
```

The administrator must select a default trunk associated with a Mediation Server. From the Topology Builder, right-click the associated Mediation Server, and then click **Properties**. Specify the default gateway for the Mediation Server. 
  

