---
title: "Include the security desk in Skype for Business Server"
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
ms.assetid: 4b1d9125-7488-419b-85dd-a8dd3ab5add3
description: "Planning how to include your organization's security desk in an E9-1-1 deployment, in Skype for Business Server Enterprise Voice."
---

# Include the security desk in Skype for Business Server
 
Planning how to include your organization's security desk in an E9-1-1 deployment, in Skype for Business Server Enterprise Voice.
  
Your company may require the security desk to become involved in an emergency call. To help decide how to integrate the Security Desk into you E9-1-1 deployment, you should answer the following questions.
  
**Do you want the security desk to be notified when there is an emergency call?**
  
You can configure the location policy so that Skype for Business Server sends instant messaging (IM) alerts to the Skype for Business SIP addresses of one or more security personnel. These alerts contain the name, number, and location of the person placing the emergency call, and facilitate security personnel in assisting with the emergency situation.
    
**Do you want to conference the security desk in on each emergency call?**
  
If supported by the emergency services service provider, you can configure the location policy to include a callback number with each emergency call. This number is then used by the provider to conference your organization's security personnel into emergency calls. This conferencing can be configured in the location policy to be one-way (listen-only) or two-way (bidirectional).
    
> [!NOTE]
> If desired, you can configure different emergency personnel for each location policy. This allows you to customize the response for different areas within your company, or create different behavior for emergency calls that originate from inside as opposed to outside the network. You can use distribution groups to specify the personnel you want to notify. 
  

