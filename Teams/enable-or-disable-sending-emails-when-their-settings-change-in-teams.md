---
title: "Enable or disable sending emails when Audio Conferencing settings change in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 26ea19d3-e420-4fc1-baa3-2692d17e5e1d
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Learn how to enable or disable Skype from sending emails to users when settings such as pin changes or the default conferencing number changes in Microsoft Teams. "
---

# Enable or disable sending emails when Audio Conferencing settings change in Microsoft Teams

Users are automatically notified by email when they are enabled for Audio Conferencing. There may be times, however, when you want to reduce the number of emails that are sent to Microsoft Teams users. In such cases, you can disable sending email.
  
If you disable sending emails, Audio Conferencing emails won't be sent to your users, including emails for when users are enabled or disabled for audio conferencing, when their PIN is reset, and when the conference ID and the default conferencing phone number changes.
  
Here is an example of the email that is sent to users when they are enabled for Audio Conferencing:
  
![Audio Conferencing email](media/teams-emails-sent-to-users-when-settings-change-image1.png)
  
## When are emails being sent to your users?

- There are several emails that are sent to users in your organization after they are enabled for audio conferencing:
    
  - When an **Audio Conferencing** license is assigned to them.
    
  - When you manually reset the user's audio conferencing PIN.
    
  - When you manually reset the user's conference ID.
    
  - When the **Audio Conferencing** license is removed from them.
    
  - When the audio conferencing provider of a user is changed from Microsoft to another provider or **None**.
    
  - When the audio conferencing provider of a user is changed to Microsoft.


## Enable or disable email from being sent to users

You can use Microsoft Teams or Windows PowerShell to enable or disable email sent to users.

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**. 

2. At the top of the **Conference Bridges** page, click **Bridge settings**. 

3. In the **Bridge settings** pane, enable or disable **Automatically send emails to users if their dial-in settings change**.

4. Click **Save**.

  
> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

**Using Windows PowerShell**
  
See the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.

    
## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
    
  
## Related topics

[Emails sent to users when their Audio Conferencing settings change](emails-sent-to-users-when-their-settings-change-in-teams.md)

[Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md)


