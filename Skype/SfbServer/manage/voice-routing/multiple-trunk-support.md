---
title: "Multiple trunk support in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server functionality supports multiple associations between gateways and Mediation Servers. These associations are made by defining a trunk, which is a logical association between a Mediation Server pool and a public switched telephone network (PSTN) gateway, Session Border Controller (SBC), or IP-PBX. Use the Topology Builder to associate gateways with Mediation Servers (that is, trunks)."
---

# Multiple trunk support in Skype for Business Server

Skype for Business Server functionality supports multiple associations between gateways and Mediation Servers. These associations are made by defining a trunk, which is a logical association between a Mediation Server pool and a public switched telephone network (PSTN) gateway, Session Border Controller (SBC), or IP-PBX. Use the Topology Builder to associate gateways with Mediation Servers (that is, trunks).

- To assign or remove a trunk in Skype for Business Server, you must first define a trunk in Topology Builder. A trunk consists of the following association: Mediation Server fully qualified domain name (FQDN), the Mediation Server listening port, the gateway FQDN, and the gateway listening port.
- To configure multiple trunks, you can create multiple associations between the same gateway and the Mediation Server. This provides additional resiliency to the Enterprise Voice infrastructure, which is especially useful in private branch exchange (PBX) interoperational scenarios. 

When a trunk is defined, it must be associated to a route. To associate a trunk to a route, you define a simple name for the trunk in Topology Builder. This simple name is used as the trunk name in the Skype for Business Server Control Panel, where trunks can be associated with routes. The simple trunk name is used as the gateway name from the Skype for Business Server Management Shell.

`New-CsVoiceRoute -Identity <RouteId> -NumberPattern <String> -PstnUsages @{add="<UsageString>"} -PstnGatewayList @{add="<TrunkSimpleName>"}`

The administrator must select a default trunk associated with a Mediation Server. From the Topology Builder, right-click the associated Mediation Server, and then click **Properties**. Specify the default gateway for the Mediation Server. 

The following diagram illustrates the multiple trunks that are defined for each Mediation Server and gateway. 

![Multiple trunk assignments](../../media/multiple-trunk-assignments.jpg)
