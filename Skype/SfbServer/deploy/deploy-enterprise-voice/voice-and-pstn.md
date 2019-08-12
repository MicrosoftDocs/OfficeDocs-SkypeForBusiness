---
title: "Configure voice policies, PSTN usage records, and voice routes in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 1e5a15f9-6f42-4dc6-baaa-24daf54afc4d
description: "Summary: Learn how to configure voice policies, PSTN usage records, and voice routes in Skype for Business Server."
---

# Configure voice policies, PSTN usage records, and voice routes in Skype for Business
 
**Summary:** Learn how to configure voice policies, PSTN usage records, and voice routes in Skype for Business Server.
  
Voice policies, PSTN usage records, and voice routes are integrally related. You configure voice policies by selecting a set of calling features and then assigning the policy a set of PSTN usage records, which specify what rights are authorized for the users or groups who are assigned the voice policy. Voice routes are also assigned PSTN usage records, which serve to match routes with the users who are authorized to use them. That is, users can only place calls that use the routes for which they have a matching PSTN usage record.
  
The recommended workflow for a new Enterprise Voice deployment is to start by configuring a voice policy that includes the appropriate PSTN usage records, and then associate the appropriate routes to each PSTN usage record. 
  
> [!NOTE]
> You can also create voice policies with  *user*  scope and assign them to individual users or groups.
  
For the detailed steps to perform each of these tasks, see the procedures in this section.
  
## In this section

- [Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md)
    
- [Configure voice mail escape in Skype for Business](configure-voice-mail-escape.md)
    
- [View PSTN usage records in Skype for Business](view-pstn-usage-records.md)
    
- [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md)
    
- [Export or import a voice route configuration file in Skype for Business](voice-route-configuration-import-export.md)
    
- [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md)
    

