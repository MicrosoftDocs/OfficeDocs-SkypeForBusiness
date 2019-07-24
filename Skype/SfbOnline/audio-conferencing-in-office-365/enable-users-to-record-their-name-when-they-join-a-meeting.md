---
title: "Enable users to record their name when they join a meeting in Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 1d649328-ada7-422d-a074-d6da4da36970
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
description: "Learn how to enable or disable whether your users can record their names when they join a meeting in Skype for Business Online."
---

# Enable users to record their name when they join a meeting in Skype for Business Online

> [!Note]
> If you want to allow users to record their names in Teams, see [Enable users to record their name when they join a meeting in Microsoft Teams](/MicrosoftTeams/enable-users-to-record-their-name-when-they-join-a-meeting-in-teams).

When you are setting up Audio Conferencing in Office 365, you will receive phone numbers and what is called an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers that can be a dedicated or shared phone number.
  
The conferencing bridge answers a call for a user who is dialing in to a meeting using a phone. The conferencing bridge answers the caller with voice prompts from an auto attendant, and then, depending on their settings, can play notifications, ask callers to record their name, and set up the PIN security for meeting organizers. PINs are given to meeting organizers to allow them to start a meeting. However, you can set it up so a PIN isn't required to start a meeting.

## Set whether callers should record their name
    
1. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
2. Under **Meeting join experience**, see the check box labeled **Enable meeting entry and exit notifications to be turned on**.
    
   - **Selected** Callers will be asked to record their name before they enter the meeting. This is selected by default.
    
   - **Cleared** Callers won't be asked to record their name before they enter the meeting.
    
3. After you make your changes, click **Save**.
    
> [!Note]
> [!INCLUDE [updating-admin-interfaces](../includes/updating-admin-interfaces.md)]

## Want to know how to manage with Windows PowerShell?

- To save time or automate this, you can use the [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715757) cmdlet.
    
- Windows PowerShell is all about managing users and what users are allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
  
## Related topics

[Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md)
