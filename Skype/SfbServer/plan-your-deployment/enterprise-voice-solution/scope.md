---
title: "Define the scope of the E9-1-1 deployment in Skype for Business Server"
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
ms.assetid: 2c572dfd-e901-471d-b5a0-18bc8d1d5328
description: "Decisions necessary for planning an E9-1-1 deployment in Skype for Business Server Enterprise Voice."
---

# Define the scope of the E9-1-1 deployment in Skype for Business Server

Decisions necessary for planning an E9-1-1 deployment in Skype for Business Server Enterprise Voice.

Before you configure Skype for Business for E9-1-1, you need to plan your E9-1-1 deployment. Some of the questions to consider include:

 **What are your organization's policy and legal obligations with regard to E9-1-1?**

 E9-1-1 legal requirements for PBXs (called Multi-line Telephone Systems, or MLTS, in E9-1-1 parlance) differ from state to state. You should consult with your legal team to understand the obligations that may apply to your deployment of Skype for Business in your relevant geographies.

 **What areas within your enterprise need to be enabled for E9-1-1?**

 You can enable E9-1-1 for the entire enterprise or for selected locations. For example, you may have varying E9-1-1 requirements for offices in different states, or you may want to exclude sites outside the U.S.

 **How will you deploy E9-1-1 to branch sites?**

 Voice resiliency is an important concept to understand when deploying E9-1-1 at a branch site. If you have centralized E-9-1-1 SIP trunks and a WAN outage occurs, clients signing in may not be able to obtain a location from Location Information service or to connect to the emergency services service provider. Skype for Business provides several strategies for handling voice resiliency in branch offices, including: having resilient data networks, deploying a SIP trunk at each branch, or pushing emergency calls out to the local gateway during outages. For details, see [Planning for Branch-Site Voice Resiliency](https://technet.microsoft.com/library/67713f57-3ded-4127-ac37-57d8099bf384.aspx).

 **Will you enable E9-1-1 for users working outside the network?**

 Automatic location acquisition is available only for clients located inside the organization's network, so your organization needs to decide whether it will support E9-1-1 calls made from Skype for Business clients while off-premises. For example, will you enable users to place emergency calls if they are working from home or from a customer site? If a client is located outside the enterprise network, the client can be configured to prompt the user for a location. However, because these user-provided locations cannot be prevalidated against the Master Street Address Guide (MSAG), the emergency services service provider dispatcher will need to confirm the validity of the location verbally with the caller before routing the call to the Public Safety Answering Point (PSAP).

> [!NOTE]
> Skype for Business clients of users who connect to your organization's network by using VPN can pick up internal IP address information, but because these addresses cannot be used to identify the user's actual location, it is essential that VPN subnets are excluded from the Location Information service.

 **Do you want to provide emergency call routing to sites outside the U.S.?**

 You may want to provide emergency routing to areas of your company not served by an emergency services service provider (for example, international locations). To do this, create a new site, and then assign voice policies to the sites that refer to a PSTN usage that routes the call through the local PSTN gateway.


