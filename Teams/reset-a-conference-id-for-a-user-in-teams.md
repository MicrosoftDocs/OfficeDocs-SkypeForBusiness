---
title: "Reset a conference ID for a user in Microsoft Teams"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 6e12242c-55f7-4bf4-90d7-0f36c0326b8e
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: Learn the steps to reset a user's meeting conference ID in Microsoft Teams, and get links to meeting update and migration tools.
---

# Reset a conference ID for a user in Microsoft Teams

A dynamic conference ID is included at the bottom of meeting invitations along with the dial-in phone numbers that can be used by callers to call in to a meeting. When the user dials the phone number, the auto attendant for the meeting will ask the caller to enter this conference ID so they can attend the meeting.
  
> [!NOTE]
> Conference IDs are generated automatically, will be between 7-9 digits, and are set when you enable Audio Conferencing for a user. **Static conference IDs aren't supported.**

## Resetting the conference ID for a user

Using the Microsoft Teams admin center:

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Click **Edit**.

3. Under **Audio Conferencing** click **Reset conference ID**.

4. In the **Reset conference ID** window, click **Reset**. A conference ID will be automatically created and an email sent to the user with the new conference ID. By default, emails are sent to users, but this can be turned off.

> [!NOTE]
> After you reset the conference ID, an email with the new conference ID will be sent to the user. This email will be sent to the primary email address, in many cases, their Microsoft 365 or Office 365 mailbox. The email contains the new conference ID, default dial-in phone number(s) and instructions for updating existing meetings.
  
> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## What else should I know?

- You can send all of the conferencing information to the user in an email that includes the conference ID and dial-in phone numbers by clicking **Send conference info in email** for the user in the **Audio Conferencing** section. It doesn't send the PIN.

- A 7- 9 digit conference ID is created by the Teams service. You can't change its length.

- After it has been reset, you can see the new conference ID listed under **Conference ID**.

- After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations.

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams/?view=teams-ps&preserve-view=true) for more information.

## Related topics

[Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin-in-teams.md)
