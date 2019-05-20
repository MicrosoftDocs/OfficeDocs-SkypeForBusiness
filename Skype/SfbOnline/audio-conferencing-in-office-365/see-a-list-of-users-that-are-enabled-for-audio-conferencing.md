---
title: "See a list of users that are enabled for Audio Conferencing in Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: bd0cd155-4c6d-424d-a2c9-af7974a2d34c
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Learn how to view a list of users in your organization that are enabled for dial-in conferencing from within the Skype for Business admin center. "
---

# See a list of users that are enabled for Audio Conferencing in Skype for Business Online

> [!NOTE]
> For information about enabled users in Microsoft Teams, see [See a list of users that are enabled for Audio Conferencing in Microsoft Teams](/MicrosoftTeams/see-a-list-of-users-that-are-enabled-for-audio-conferencing-in-teams).

After you have enabled Skype for Business users in your organization for Audio Conferencing, you can view the list of those users who have been enabled. When you look at the list, you will also see for each user in the list the type of audio conferencing provider that they are using, the default dial-in phone number for the user, and if you organization isn't enabled for dynamic conference IDs, the static conference IDs for audio conferencing meetings that they organize.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](../includes/updating-admin-interfaces.md)]
  
## Viewing a list of users

   
- In the left navigation, go to **Audio conferencing** > **Users**.

## What else should I know?

- When you view the list of users that are enabled, you can select a user from the list and use the Action pane to edit the audio conferencing settings for that user.
    
- When you select a single user that is configured to use Microsoft as the audio conferencing provider, you can view the default phone number and whether your organization is enabled for dynamic conference IDs, and you can reset the conference ID for meetings that the user organizes.
    
- When you select a single user who is configured to use a third-party audio conferencing provider, you can view the name of the audio conferencing provider, the toll phone number, and the toll-free phone number (if they are set up).
    
- You can use the filter options to show users that have:
    
  - **Audio conferencing on**
    
  - **Audio conferencing off**
    
  - **Conferencing provider - Microsoft**
    
  - **Conferencing provider - others**
    
- You can use the search button to search for an individual user in the list.
    
- You can select more than one user and do the following:
    
  - Select a different default number for these users.
    
  - Turn off audio conferencing for the user by changing the provider to **None**.
    
  - Switch to Microsoft as the audio conferencing provider if the user has been assigned an **Audio Conferencing** license.
    
  - Allow/disallow anonymous users to activate the selected users' phone meetings.
    
## Want to know how to manage with Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
## Related topics

[Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md)
