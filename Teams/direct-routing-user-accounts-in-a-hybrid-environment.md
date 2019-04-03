---
title: "User accounts in a hybrid environment with PSTN connectivity"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
appliesto: Microsoft Teams
description: "Learn about different combinations of user creation and which combinations are supported or unsupported."
---

# User accounts in a hybrid environment with PSTN connectivity

## About the environment

This article applies to environments in which you have all of the following: 
 
- Skype for Business Server or Lync Server 2013 
- An Office 365 tenant 
- Hybrid connectivity configured between the Skype for Business Server and Skype for Business Online or Microsoft Teams tenant 
- Users who are enabled to make and receive Public Switched Telephone Network (PSTN) calls to and from the client

 
If you have a different environment (such as Skype for Business Cloud Connector Edition), hybrid is not configured, or your users are not enabled for PSTN calls, the supportability matrix will be different.  

## About the combinations and the supportability statement  

A Skype for Business hybrid environment with PSTN connectivity provides flexibility regarding where user services are provided and how user accounts are provisioned and managed. But the abundance of options might create some unsupported combinations. This section explains different combinations of user creation, followed by a supportability statement.


**Definitions:**   
- **Enterprise Voice:** Option to provide access to PSTN for users with on-premises Skype for Business user account. On-premises Skype for Business Mediation server provides interconnectivity to PSTN.  
- **Hybrid Voice Connectivity:** Option to provide access to PSTN for users with Skype for Business Online account. On-premises Skype for Business Mediation server provides interconnectivity to PSTN. 
- **Direct routing:** Option to provide access to PSTN for users with online Skype for Business account, Microsoft Teams license, using Microsoft Teams client. The SBC is connected to the SIP Proxy in Office 365 without need for any on-premises software from Microsoft.

  
**The environment supports the following combinations:**
- **Scenario 1:** User account in Skype for Business on-premises and will use the Skype for Business client with Enterprise Voice
- **Scenario 2:** User account in Skype for business online and will use the Skype for Business client with Hybrid Voice Connectivity
- **Scenario 3:** User account in Skype for Business online with Microsoft Teams license and will use Teams client
 
### Supportability matrix


|**User object created in**  |**User’s Skype for Business service provider**|**User’s Client**|**Voice option**|**Supported**|
| ------------ | --------- | --------- | --------- | -------- |
|On premises AD| On premises |Skype for Business   | Enterprise Voice   |Yes|
|On premises AD|Online| Skype for Business  | Hybrid Voice Connectivity   |Yes |
|On premises AD|Online |Microsoft Teams |Direct Routing  |Yes |
|**Unsupported combinations**    | |         |         |      |
|Azure AD| On premises/online | Skype for Business/Microsoft Teams|Enterprise Voice/Hybrid Voice Connectivity/Direct Routing  |No, user object MUST be created in on-premises AD first |
|On premises AD  |On premises| Microsoft Teams| Enterprise Voice/Hybrid Voice Connectivity/Direct Routing   |No, Microsoft Teams client is not supported with on-premises Skype for Business |     
|On premises AD  |Online |Skype for Business  | Direct Routing  |No, Direct Routing is not supported with Skype for Business client, and user must be enabled for Enterprise Voice in Skype for Business first  |


### Supportability statement for the hybrid environment with PSTN

For all users, the user object **must** be created in the on-premises AD and synchronized to the Azure AD using the Azure AD Connect tool. Enabling users for Teams/Skype for Business **is not supported** if the user object is created directly in the Azure AD in a hybrid configuration. For new users, such as a new hire, who will be enabled directly for Teams, the user must be enabled for Skype for Business using on premises Skype for Business management tools. Creating users in online Skype for Business or Teams without first enabling them in on-premises pool with Enterprise Voice **is not supported**. For more information on this, look into [Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity).
