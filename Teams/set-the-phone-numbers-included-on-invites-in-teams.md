---
title: "Set the phone numbers included on invites in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 32954439-d365-4125-872f-b37466ecb035
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Get the steps to create a default phone number for callers to join a Microsoft Teams meeting. "
---

# Set the phone numbers included on invites in Microsoft Teams

Audio Conferencing in Office 365 enables users in your organization to create Microsoft Teams meetings, and then allow users to dial in to those meetings using a phone. In Office 365, you have the option of using a Microsoft audio conferencing bridge or a third-party audio conferencing bridge that is hosted by an approved audio conferencing provider (ACP).
  
A conferencing bridge gives you a set of dial-in phone numbers for your organization. All of them can be used to join the meetings that a meeting organizer has created, but you can select which ones will be included on their meeting invites.
  
> [!NOTE]
> There can be a maximum of one toll and one toll-free phone number on the meeting invite for a meeting organizer, but there is also a link located at the bottom of each meeting invite that opens the full list of all dial-in phone numbers that can be used to join a meeting. 

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Set or change the default audio conferencing phone number for a meeting organizer or user

![teams-logo-30x30.png](media/teams-logo-30x30.png) Using the Microsoft Teams and Skype for Business Admin Center

1. In the left navigation, click **Users**, and then select the user from the list of available users.

    ![Shows selecting users in the Microsoft Teams and Skype for Business Admin Center](media/teamsselectusers.png)

2. At the top of the page, click **Edit**.

    ![Click Edit in the Microsoft Teams and Skype for Business Admin Center](media/teamsedituser.png)

3. Next to **Audio Conferencing**, click **Edit**. 
    
    ![Click Edit next to Audio conferencing](media/teamseditaudioconf.png)

4. Use the **Toll number** or **Toll-free number** fields to enter the numbers for the user.


> [!IMPORTANT]
> When you change a user's audio conferencing settings, recurring and future Microsoft Teams meetings must be updated and sent to attendees. 

## Want to use Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information. 
  
    
## Related topics

[Try or purchase Audio Conferencing in Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)
