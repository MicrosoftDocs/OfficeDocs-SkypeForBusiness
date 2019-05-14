---
title: "Reset the Audio Conferencing PIN in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 67866a47-89c1-4593-8766-3a68777e2be6
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Find out what you should know about PINs and how to reset them in Microsoft Teams. "
---

# Reset the Audio Conferencing PIN in Microsoft Teams

A PIN is a code made up of numbers that is created for each Microsoft Teams user who is enabled for audio conferencing. Audio conferencing PINs are used by meeting organizers to identify that they are the meeting organizer and allow them to start a meeting over the phone. If they use the Microsoft Teams app to start the meeting, a PIN isn't required. If users forget their PIN and they can't find it in the email that was sent to them when they were enabled for audio conferencing, an administrator can reset their PIN, or they can reset their own PIN.
  
Meetings can be started when an authenticated user joins using the Microsoft Teams app or when the organizer joins with his or her PIN over the phone. When a meeting requires a PIN to start, users who join over the phone will be placed in the lobby and will listen to music on hold until the meeting starts. If the organizer of a meeting doesn't require a PIN to start the meeting over the phone, then callers won't be asked to provide a PIN when they join the meeting.

## Reset a user's PIN

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Click **Edit**.

3. Under **Audio Conferencing**, click **Reset PIN**.

4. Click **Reset**.
 
> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
   
## Have a user reset his or her own PIN

1. Have the user go to [https://admin0m.online.lync.com/lscp/usp/pstnconferencing](https://admin0m.online.lync.com/lscp/usp/pstnconferencing).
2. Click **Reset PIN**. 


## What else should you know about PINs?

- For security purposes, the PIN is only shown to an administrator on one time, when the PIN is reset. After the PIN is reset by an administrator, the PIN will be listed as ***********.
    
- Automatically sending emails to users is enabled by default, and users will receive an email with their PIN when they're enabled for audio conferencing or when the PIN is reset. But if you have disabled automatically sending emails, a PIN reset email won't be sent to a user and you will have to manually send the PIN information to the user.
    
- When a meeting starts, all of the users in the lobby will automatically join it. For example, if two participants try to join a meeting before it has been started, they will be put in the lobby and will listen to music on hold, and when the meeting organizer joins using his PIN via phone, the meeting will start and the participants in the lobby will join the meeting.
    
- The default setting is to not allow a meeting to be started by anonymous callers.
    
- When you enable a user for audio conferencing, by default they are sent emails that include conferencing information and their PIN. The user must have an Office 365 mailbox, because when a PIN is reset, a new PIN will be sent to the user in email to their primary SMTP address (alias) that is set for the user.
    
- When you set up audio conferencing, you set the digits that are required for the PINs in your organization. PINs can be from 4 to 12 digits - the default is 5. If you change the PIN length setting, the setting is only applied on newly generated PINs and isn't applied to the PIN setting for existing users that are enabled for audio conferencing. See [Set the length of the PIN for Audio Conferencing meetings](Set-the-PIN-length-for-Audio-Conferencing-meetings-in-teams.md).
    
- The email by default will be set to the Office 365 primary SMTP address of the user. You can send an email to a non-Office 365 address such as a Hotmail or MSN email address. You can override the default email address by using Windows PowerShell. This is useful if the users don't have an Exchange mailbox in Office 365.

    

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
  
## Related topics

[Reset a conference ID for a user](reset-a-conference-id-for-a-user-in-teams.md)
