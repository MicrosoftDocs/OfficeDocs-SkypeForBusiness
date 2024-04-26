---
title: "Reset the Audio Conferencing PIN in Microsoft Teams"
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/21/2024
ms.topic: article
ms.assetid: 67866a47-89c1-4593-8766-3a68777e2be6
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-apr2020
description: Learn how to reset a user's Audio Conferencing PIN in Microsoft Teams, and learn important facts about PINs.
---

# Reset the Audio Conferencing PIN in Microsoft Teams

A PIN is a code made up of numbers that is created for each Microsoft Teams user who is enabled for audio conferencing. Audio conferencing PINs are used by meeting organizers to identify that they're the meeting organizer and allow them to start a meeting over the phone. If they use the Microsoft Teams app to start the meeting, a PIN isn't required. If users forget their PIN and can't locate it in their activation email, an admin can reset it. Users can also reset their own PIN.
  
Meetings can be started when an authenticated user joins using the Microsoft Teams app or when the organizer joins with their PIN over the phone. When a meeting requires a PIN to start, users who join over the phone are placed in the lobby. These users listen to music on hold until the organizer admits them. If the organizer of a meeting doesn't require a PIN to start the meeting over the phone, then callers aren't asked to provide a PIN when they join the meeting.

## Reset a user's PIN

Using the Microsoft Teams admin center:

1. In the left navigation, select **Users**, and then select the user from the list of available users.

2. Select **Edit**.

3. Under **Audio Conferencing**, select **Reset PIN**.

4. Select **Reset**.

> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Have a user reset their own PIN

1. Have the user go to [https://dialin.teams.microsoft.com/usp](https://dialin.teams.microsoft.com/usp).
2. Select **Reset PIN**.

> [!NOTE]
> For GCCH go to: [https://dialin.cpc.gov.teams.microsoft.us/usp](https://dialin.cpc.gov.teams.microsoft.us/usp).
> For DoD go to: [https://dialin.cpc.dod.teams.microsoft.us/usp](https://dialin.cpc.dod.teams.microsoft.us/usp).

> [!NOTE]
> A PIN reset email won't be sent to the user if using this method.

## What else should you know about PINs?

- For security purposes, the PIN is only shown to an administrator one time, when the PIN is reset. After an admin resets the PIN, the PIN is listed as ***********.

- Automatically sending emails to users is enabled by default. When users enabled for audio conferencing or when their PIN is reset, they receive an email. If you disable automatically sending emails, PIN reset emails aren't sent to the user and you have to manually send the PIN information to the user.

- When a meeting starts, the organizer needs to admit all Public Switched Telephone Network (PSTN) users in the lobby to join the meeting. If two PSTN participants attempt to join a meeting that already started, they're placed in the lobby with hold music. When the meeting organizer joins via phone using their PIN, they can start the meeting and use the in-meeting command (*21) to admit all PSTN users in the lobby.

- The default setting is to not allow anonymous callers to start a meeting.

- When you enable a user for audio conferencing, by default they're sent emails that include conferencing information and their PIN. The user must have a Microsoft 365 or Office 365 mailbox. When you reset a PIN, the new one is emailed to the user's primary Simple Mail Transfer Protocol (SMTP) address (alias).

- When you set up audio conferencing, you set the digits that are required for the PINs in your organization. PINs can be from 4 to 12 digits - the default is 5. If you change the PIN length setting, the setting is only applied on newly generated PINs.  The setting isn't applied to the PIN setting for existing users that are enabled for audio conferencing. For more information, see [Set the length of the PIN for Audio Conferencing meetings](Set-the-PIN-length-for-Audio-Conferencing-meetings-in-teams.md).

- The email by default is set to the Microsoft 365 or Office 365 primary SMTP address of the user. You can send an email to a non-Microsoft 365 or non-Office 365 address such as a Hotmail or MSN email address. You can override the default email address by using Windows PowerShell. This is useful if the users don't have an Exchange mailbox in Microsoft 365 or Office 365.

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 by using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams).
  
## Related topics

- [Reset a conference ID for a user](reset-a-conference-id-for-a-user-in-teams.md)
