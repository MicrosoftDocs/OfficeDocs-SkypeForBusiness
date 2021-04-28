---
title: "How can caller ID be used in your organization"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: mikedav, roykuntz
ms.topic: article
ms.assetid: 5a0bd8ba-3334-46ee-becf-1025597737f6
ms.tgt.pltfrm: cloud
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

Caller ID consists of two user-facing identifiable pieces of information:

- A phone number (typically referred to as CLID or calling line ID). This is the Public Switched Telephone Number (PSTN) presented as the identification of the caller.

- A Calling party name (typically referred to as CNAM), which can be up to 15 characters in length. 

You can control Caller ID for both inbound and outbound calls for Phone System users by using a policy called CallingLineIdentity. You can also control the company name associated with the outbound call, the Calling Party Name or CNAM. For more information, see [More about Calling Line ID and Calling Party Name](more-about-calling-line-id-and-calling-party-name.md.)
  
The caller ID functionality is available to all Phone System users regardless of PSTN connectivity:

- Microsoft Calling Plans 

- Phone System Direct Routing 
  
  
## Outbound caller ID

For presenting the outbound PSTN caller ID, the following options are available:
  
- The telephone number assigned to the user, which is the default.

- Anonymous, which is possible by removing the presentation of the user’s PSTN number. 

- Substituting the users caller ID with a different phone number:

  - A telephone number that is classified as a service and toll-free number in your Calling Plans telephone number inventory. It is usually assigned to an Teams Auto Attendant or Call Queue.

  - An on-premises telephone number via Direct Routing that is assigned to a resource account used by a Teams Auto Attendant or Call Queue.

In addition, you can also specify the Calling Party Name or CNAM set on the outbound PSTN call.
    
To set the outbound caller ID, see [Set the Caller ID for a user](./set-the-caller-id-for-a-user.md).
  
### End user control of outbound caller ID

Users can change their caller ID setting to **Anonymous** by setting the EnableUserOverride attribute. 

If the outbound caller ID is set to Anonymous, the EnableUserOverride has no effect and the caller ID is always set to Anonymous. The default value of EnableUserOverride is False.

Your end users can set their caller ID to Anonymous by going to Settings > Calls, and then under Caller ID, select Hide my phone number and profile information for all calls.

### Notes

Keep the following in mind:

- You can't assign the following types of phone numbers for the outbound caller ID:

  - Any phone numbers that are classified as a user in your Calling Plans telephone number inventory.

  - Any on-premises telephone number via Direct Routing that is assigned to a user.

  - A Skype for Business Server on-premises telephone number.

- The use of resource account phone number substitution only works for Teams users. The substitution of service phone number works for both Skype for Business Online and Teams users.

- Calling Party Name is only sent on calls where the caller ID is substituted with LineUri, a service or resource account phone number and when the caller is a Teams user.

- Calling Party Name can have a maximum of 200 characters.

- For Direct Routing, the phone number substitution and the Calling Party Name is sent in the FROM SIP header. If the corresponding OnlinePstnGateway is configured with ForwardPai = True, the P-ASSERTED-IDENTITY SIP header will contain the real calling user.

- EnableUserOverride has preference to other settings in the policy, except if substitution is set to Anonymous. For instance, if a policy instance has substitution using a resource account and EnableUserOverride is set and enabled by the user, then the outbound caller ID will be blocked and Anonymous will be used. If a policy instance has substitution set to Anonymous and EnableUserOverride is set, the outbound caller ID will always be Anonymous, no matter the end user setting.

This only applies when a CallingLineIdentity policy is configured with a CallingIDSubstitute parameter of either LineURI or Substitute. The default value of EnableUserOverride is False.
  

   
## Inbound caller ID

Phone System will show the incoming external phone number as the caller ID. If the number is associated with a user or contact in Azure AD or a personal contact, the Teams client will show the caller ID based on that information. If the phone number is not in Azure AD or a personal contact, the telco-provided display name will be shown if it is available.

The BlockIncomingCallerID attribute allows for blocking the caller ID on incoming PSTN calls. You can set this attribute, but it isn't available to your end users on the user settings page. When this setting is enabled the incoming PSTN caller will be displayed as coming from Anonymous.
  
To set the outbound caller ID, see [Set the Caller ID for a user](./set-the-caller-id-for-a-user.md).
  
## Related topics
[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](./different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
