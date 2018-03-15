---
title: "Enabling users for E9-1-1 in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3cc64f5b-492e-4c47-9713-3c376f2aad02
description: "During client registration, Lync Server uses a location policy to configure the E9-1-1 properties for Enterprise Voice-enabled users. This policy contains the settings that define how E9-1-1 is implemented. For example, the location policy contains information such as the emergency dial string, and whether or not a user is required to manually enter a location if the Location Information service does not automatically provide one. For a complete definition of a location policy, see Defining the location policy for Lync Server 2013."
---

# Enabling users for E9-1-1 in Lync Server 2013
[]
During client registration, Lync Server uses a location policy to configure the E9-1-1 properties for Enterprise Voice-enabled users. This policy contains the settings that define how E9-1-1 is implemented. For example, the location policy contains information such as the emergency dial string, and whether or not a user is required to manually enter a location if the Location Information service does not automatically provide one. For a complete definition of a location policy, see [Defining the location policy for Lync Server 2013](defining-the-location-policy.md).
  
Lync Server can assign a location policy to clients based on subnet, or to users based on a global, per-site, or per-user policy. To help decide how you will enable users, you should first answer the following questions.
  
 **Do you plan to enable all users, or limit support to specific geographic areas of the enterprise?**
  
> You can assign a location to all users in your enterprise by using a global location policy. However, by assigning a location policy to a Lync Server network site and then adding subnets to the site, you can limit E9-1-1 support to selected locations within the enterprise and specify E9-1-1 routing behavior on a per-site basis. 
    
 **Do you plan to enable individual users through a user policy?**
  
> You can assign location policies directly to specific users or common area phone contact objects if you want to customize their E9-1-1 support.
    
 **When clients roam outside the network or connect from an undefined subnet, should the clients still be enabled for E9-1-1?**
  
> If users are assigned a global, site, or per-user location policy, they can be required to manually enter a location into the client if the client is not located within a defined subnet or no location has been found by the Location Information service. For details, see [Defining the user experience for manually acquiring a location in Lync Server 2013](defining-the-user-experience-for-manually-acquiring-a-location.md).
    

