---
title: "Enable users for E9-1-1 in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 3cc64f5b-492e-4c47-9713-3c376f2aad02
description: "Decisions necessary for the location policy for an E9-1-1 deployment in Skype for Business Server Enterprise Voice, including which users to enable and how to support roaming users."
---

# Enable users for E9-1-1 in Skype for Business Server
 
Decisions necessary for the location policy for an E9-1-1 deployment in Skype for Business Server Enterprise Voice, including which users to enable and how to support roaming users.
  
During client registration, Skype for Business Server uses a location policy to configure the E9-1-1 properties for Enterprise Voice-enabled users. This policy contains the settings that define how E9-1-1 is implemented. For example, the location policy contains information such as the emergency dial string, and whether or not a user is required to manually enter a location if the Location Information service does not automatically provide one. For a complete definition of a location policy, see [Plan location policies for Skype for Business Server](location-policies.md).
  
Skype for Business Server can assign a location policy to clients based on subnet, or to users based on a global, per-site, or per-user policy. To help decide how you will enable users, you should first answer the following questions.
  
 **Do you plan to enable all users, or limit support to specific geographic areas of the enterprise?**
  
> You can assign a location to all users in your enterprise by using a global location policy. However, by assigning a location policy to a Skype for Business Server network site and then adding subnets to the site, you can limit E9-1-1 support to selected locations within the enterprise and specify E9-1-1 routing behavior on a per-site basis. 
    
 **Do you plan to enable individual users through a user policy?**
  
> You can assign location policies directly to specific users or common area phone contact objects if you want to customize their E9-1-1 support.
    
 **When clients roam outside the network or connect from an undefined subnet, should the clients still be enabled for E9-1-1?**
  
> If users are assigned a global, site, or per-user location policy, they can be required to manually enter a location into the client if the client is not located within a defined subnet or no location has been found by the Location Information service. For details, see [Define the user experience for manually acquiring a location in Skype for Business Server](manually-acquiring-a-location.md).
    

