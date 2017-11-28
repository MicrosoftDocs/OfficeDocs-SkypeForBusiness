---
title: "Calling Plans known issues"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.custom: Adm_O365_FullSet
ms.assetid: baa3645a-0518-472e-942e-971c63ba4ca0

description: "Learn known issues with the calling plan for Office 365 (PSTN Calling) and what you can do about them. "
---

# Calling Plans known issues

Calling Plans in Office 365 are a new feature found in Skype for Business Online. The following are current issues that are being tracked and actively investigated. They will be potentially resolved when the feature is updated in future builds in Office 365 and Skype for Business Online.
  
## Calling Plans known issues

|**Known issue**|**Comments**|
|:-----|:-----|
|Transitioning from Tech Preview licenses to production licenses for Calling Plans don't automatically update the license.  <br/> |Purchase your new licenses first so they are ready to be assigned to your users. Remove the promo (Tech Preview) license from a user, and then **IMMEDIATELY** assign the new **Domestic Calling Plan** and/or **International Calling Plan** licenses to the user. <br/> If you are removing and adding licenses for multiple users, it is extremely important that you remove the licenses from all of the users using Windows PowerShell and then **IMMEDIATELY** assign the licenses for all of the users also using Windows PowerShell. Doing this will ensure that there is no disruption in service when handling large volumes of user license assignments. For sample PowerShell scripts, see[Assign Skype for Business and Microsoft Teams licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).  <br/> > [!NOTE]> If you are using on-premises PSTN connectivity for hybrid users, you  *only*  need to assign a **Phone System** license. You should **NOT** also assign a voice Calling Plan.> However, if you are enabling Calling Plans in Office 365 for users that are in Office 365, you need to still assign a **Domestic Calling Plan** and/or **International Calling Plan** license for those users. See[Assign Skype for Business and Microsoft Teams licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).           |
   
## Related Topics

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
  
[Audio Conferencing complimentary dial-out period](../accessibility-and-regulatory/audio-conferencing-complimentary-dial-out-period.md)
  

