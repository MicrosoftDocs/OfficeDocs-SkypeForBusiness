---
title: "Turn on or off entry and exit announcements for meetings"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/22/2018
ms.topic: article
ms.assetid: f2c7b5ea-07b6-4b77-8023-bec9596fcc32
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing 
description: "Learn how to turn entry and exit announcements on or off in a Skype for Business Online meeting using the Skype for Business admin center. "
---

# Turn on or off entry and exit announcements for meetings

When you are setting up Audio Conferencing in Office 365, you will get an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers that people will use to call in to a Skype for Business or Microsoft Teams meeting. 
  
The conferencing bridge answers a call for a user who is dialing in to a meeting using a phone. The conferencing bridge answers the caller with voice prompts from a conferencing auto attendant, and then, depending on your settings, can play notifications, ask callers to record their name, and set up the PIN security. A PIN is given to a Skype for Business or Microsoft Teams meeting organizer, and it allows them to start a meeting if they can't start the meeting using a Skype for Business or Microsoft Teams app. You can, however, set it so that a PIN isn't required to start a meeting.
  
## Setting meeting join options

**Using the Microsoft Teams and Skype for Business Admin Center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**. 

2. At the top of the **Conference Bridges** page, click **Bridge Settings**. 

3. In the **Bridge settings** pane, enable or disable **Enable meeting entry and exit notifications to be turned on**. This is selected by default. If you clear it, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.
    
4. Under **Entry/exit announcement type**, select **Names or phone numbers** or **Tones**.
    
5. Enable or disable **Ask callers to record their name before joining the meeting**.
    
6. After you make your changes, click **Apply**.

**Using the Skype for Business admin center**
    
1. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
2. Under **Meeting join experience**, select or clear **Enable meeting entry and exit notifications to be turned on**. This is selected by default. If you clear it, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.
    
3. Under **Entry/exit announcement type**, select **Names or phone numbers** or **Tones**.
    
4. Check or uncheck **Ask callers to record their name before joining the meeting**.
    
5. After you make your changes, click **Save**.
    
## Want to know how to manage with Windows PowerShell?

- To save time or automate this, you can use the [Set-CsOnlineDialInConferencingBridge](https://go.microsoft.com/fwlink/?LinkId=617686 ) cmdlet.
    
-  When it comes to Windows PowerShell, Skype for Business Online is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making settings changes for many users at one time. Learn about these advantages in the following topics: 
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
  
## Related topics

[Audio Conferencing common questions](audio-conferencing-common-questions.md)

## Feedback?
To provide product feedback or to let us know how we're doing, see [Skype for Business Feedback](https://www.skypefeedback.com).