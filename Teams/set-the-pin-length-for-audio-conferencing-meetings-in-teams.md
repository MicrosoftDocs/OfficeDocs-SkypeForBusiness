---
title: "Set the PIN length for Audio Conferencing meetings in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: b86d31c6-1543-478f-b8c6-4b71e708403a
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Learn the parameters for the length and requirements of a PIN and see how to set the length for meetings in Microsoft Teams."
---

# Set the PIN length for Audio Conferencing meetings in Microsoft Teams

When you are setting up audio conferencing for Microsoft Teams, you will get an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. The phone number you set will be included on the meeting invites for the Microsoft Teams app.
  
The audio conferencing bridge answers a call for people who are dialing in to a meeting using a phone. It answers the caller with voice prompts from an auto attendant and then, depending on your settings, can play notifications and ask callers to record their name. **Microsoft bridge settings** allow you to change the settings for meeting notifications and the meeting join experience, and set the length of the PINs that are used by meeting organizers. Meeting organizers use PINs to start meetings if they can't join the meeting using the Microsoft Teams app.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Setting the PIN length

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**. 

2. At the top of the **Conference Bridges** page, click **Bridge Settings**. 

3. In the **Bridge settings** pane, under **PIN length**, select the number of digits you want for the PIN.

4. Click **Save**.

> [!NOTE]
> A PIN is different from a conference ID. Conference IDs are used by callers when they join the meeting. They are used to identify the meeting. The PIN is used to authenticate a caller as the meeting organizer. 

## Want to know more about PIN settings?

- PINs can be from 4 to 12 digits; the default is 5. Numbers are only used when creating PINs. Letters and special characters aren't used.
    
- A PIN is only required for the meeting organizer when a Microsoft Teams user hasn't already started the meeting. If everyone is dialing in to the meeting, then the PIN is required for the meeting organizer to start the meeting.
    
- PIN security settings are applied to all of the phone numbers that are associated with a Microsoft bridge. They will be applied to all meetings that use the phone numbers associated with a given bridge. 
    
## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
    
  
## Related topics

[Try or purchase Audio Conferencing in Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)
