---
title: "Assign location policy scope in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: e4c66517-c593-4253-b900-7b4dd8bddf2f
description: "Planning location policies for an E9-1-1 deployment in Skype for Business Server Enterprise Voice."
---

# Assign location policy scope in Skype for Business Server
 
Planning location policies for an E9-1-1 deployment in Skype for Business Server Enterprise Voice.
  
As with other Skype for Business Server policies, location policies can be assigned at multiple scope levels: global, site, and user. However, the scope of user-level location policies behaves a bit differently than with other Skype for Business Server policies. Not only can per-user location policies be applied to endpoint objects (such as Users and Common Area Phone contact objects), they can also be applied to Skype for Business Server network sites. Network sites are groupings of client subnets associated with a geographical location (but may not necessarily be all subnets in an entire central site or branch site). Any clients connected to the subnets in a network site automatically pick up the location policy assigned to that network site. In cases where a user-level location policy is assigned both to a user and to a network site, the network site-based location policy overrides any per-user policy setting.
  
Each network site has a location policy assigned to it, and each policy will have different PSTN Usages, Notification URIs, and Conference URIs values assigned to it.
  
> [!NOTE]
> The reason for this special policy scoping behavior is so that when a user homed on a pool at one office site visits another site and has to make an emergency call, the E9-1-1 call routing settings appropriate to that network site will apply no matter what pool or site the user is assigned to. 
  

