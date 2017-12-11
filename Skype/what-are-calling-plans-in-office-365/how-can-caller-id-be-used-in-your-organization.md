---
title: "How can caller ID be used in your organization"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.date: 12/15/2017
ms.topic: article
ms.assetid: 5a0bd8ba-3334-46ee-becf-1025597737f6
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
ms.appliesto: 
- Skype for Business
- Microsoft Teams
localization_priority: Normal
ROBOTS: None
f1keywords: None
ms.custom:
- Calling Plans
- Strat_SB_PSTN
description: "Caller ID can be controlled for both inbound and outbound calls for Phone System users by using a policy called CallingLineIdentity."
---

# How can caller ID be used in your organization

Caller ID can be controlled for both inbound and outbound calls for Phone System users by using a policy called CallingLineIdentity.
  
The Caller ID functionality is available to all Phone System users regardless of PSTN connectivity:
  
- Online PSTN Connectivity
    
- On-Premises PSTN Connectivity with Skype for Business Cloud Connector Edition (requires Cloud Connector Edition 1.4.2 and beyond)
    
- On-Premises PSTN Connectivity with Skype for Business Server (requires Skype for Business Server 2015 CU5 and beyond)
    
> [!NOTE]
> This policy isn't available in Skype for Business 2015 Server. 
  
## Outbound caller ID

There are three options available for outbound PSTN Caller ID:
  
- The telephone number assigned to the user, which is the default.
    
- A telephone number that is classified as a *service* and *toll-free* number in your Calling Plans in Office 365 telephone number inventory. It is usually assigned to an organizational auto attendant or call queue.
    
- Set to anonymous.
    
However, you can't assign these types of phone numbers for the outbound caller ID:
  
- Any phone numbers that are classified as a  *user*  in your Calling Plans telephone number inventory
    
- A Skype for Business Server on-premises phone number
    
To set the outbound caller ID, see [Set the Caller ID for a user](set-the-caller-id-for-a-user.md).
  
### End User Control of Outbound Caller ID

The EnableUserOverride attribute enables single or multiple users to change their Caller ID setting to **Anonymous**. This only applies when a CallingLineIdentity policy is configured with a CallingIDSubstitute parameter of either LineURI or Substitute. The default value of EnableUserOverride is False.
  
Your end users can set their caller ID to **Anonymous** by using the **Call Forward Settings** tab in the Skype for Business desktop client.
  
||||
|:-----|:-----|:-----|
|**Windows** <br/> |**Version** <br/> |**Supported** <br/> |
|Click-to-Run  <br/> |Current Channel released on December 6, 2016 - version 1611 (Build 7571.2072)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |First Release for Deferred Channel released on February 22, 2017 - Version 1701 (Build 7766.2060)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |Deferred Channel released on June 13, 2017 - Version 1701 (Build 7766.2092)  <br/> |Yes  <br/> |
|MSI  <br/> |Skype for Business  <br/> |No  <br/> |
|Mac  <br/> |Skype for Business  <br/> |No  <br/> |
   
Your end users can also set their caller ID setting on the user settings page at: [https://mysettings.lync.com/pstncalling](https://mysettings.lync.com/pstncalling).
  
## Inbound Caller ID

The BlockIncomingCallerID attribute allows for blocking the caller ID on incoming PSTN calls. You can set this attribute, but it isn't available to your end users on the user settings page. And it is currently available only with Online PSTN connectivity.
  
To set the outbound caller ID, see [Set the Caller ID for a user](set-the-caller-id-for-a-user.md).
  
## Related topics
[Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://go.microsoft.com/fwlink/?LinkID=692099)