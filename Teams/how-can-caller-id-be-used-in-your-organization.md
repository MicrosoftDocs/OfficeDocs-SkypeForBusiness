---
title: "How can caller ID be used in your organization"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: mikedav, roykuntz
ms.topic: article
ms.assetid: 5a0bd8ba-3334-46ee-becf-1025597737f6
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
  - ms.teamsadmincenter.voice.callerid.overview
description: "Caller ID can be controlled for both inbound and outbound calls for Phone System users by using a policy called CallingLineIdentity."
---

# How can caller ID be used in your organization

Caller ID can be controlled for both inbound and outbound calls for Phone System users by using a policy called CallingLineIdentity.
  
The caller ID functionality is available to all Phone System users regardless of PSTN connectivity:

- Microsoft Calling Plans 

- Phone System Direct Routing 
  
- Online PSTN Connectivity
    
- On-Premises PSTN Connectivity with Skype for Business Cloud Connector Edition (requires Cloud Connector Edition 1.4.2 and beyond)
    
- On-Premises PSTN Connectivity with Skype for Business Server (requires Skype for Business Server 2015 CU5 and beyond)
    
> [!NOTE]
> This policy isn't available in Skype for Business 2015 Server. 
  
## Outbound caller ID

There are three options available for outbound PSTN caller ID:
  
- The telephone number assigned to the user, which is the default.
    
- A telephone number that is classified as a *service* and *toll-free* number in your Calling Plans telephone number inventory. It is usually assigned to an organizational auto attendant or call queue.
    
- Set to anonymous.
    
However, you can't assign these types of phone numbers for the outbound caller ID:
  
- Any phone numbers that are classified as a  *user*  in your Calling Plans telephone number inventory
    
- A Skype for Business Server on-premises phone number
    
To set the outbound caller ID, see [Set the Caller ID for a user](./set-the-caller-id-for-a-user.md).
  
### End user control of outbound caller ID

The EnableUserOverride attribute enables single or multiple users to change their caller ID setting to **Anonymous**. This only applies when a CallingLineIdentity policy is configured with a CallingIDSubstitute parameter of either LineURI or Substitute. The default value of EnableUserOverride is False.
  
Your end users can set their caller ID to **Anonymous** by using the **Settings** tab in the Skype for Business desktop client, select **Calls an End User** (if enabled by admin), and then select **Hide my phone number and profile information for all calls**. In Teams, users can go to their profile picture in the upper-right corner, select **Settings** > **Calls**,  and then under **Caller ID**, select **Hide my phone number and profile information for all calls**.
  
||||
|:-----|:-----|:-----|
|**Windows** <br/> |**Version** <br/> |**Supported** <br/> |
|Click-to-Run  <br/> |Current Channel released on December 6, 2016 - version 1611 (Build 7571.2072)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |First Release for Deferred Channel released on February 22, 2017 - Version 1701 (Build 7766.2060)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |Deferred Channel released on June 13, 2017 - Version 1701 (Build 7766.2092)  <br/> |Yes  <br/> |
|MSI  <br/> |Skype for Business  <br/> |No  <br/> |
|Mac  <br/> |Skype for Business  <br/> |No  <br/> |
   
## Inbound caller ID

Phone System will show called ID for an external phone number if the number is associated with a user in Azure AD. If the phone number is not in Azure AD, the telco-provided display name will be shown if it is available.

The BlockIncomingCallerID attribute allows for blocking the caller ID on incoming PSTN calls. You can set this attribute, but it isn't available to your end users on the user settings page. And it is currently available only with Online PSTN connectivity.
  
To set the outbound caller ID, see [Set the Caller ID for a user](./set-the-caller-id-for-a-user.md).
  
## Related topics
[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](./different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
