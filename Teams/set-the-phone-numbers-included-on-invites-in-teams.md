---
title: Set the phone numbers included on invites
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/22/2024
ms.topic: article
ms.assetid: 32954439-d365-4125-872f-b37466ecb035
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
  - seo-marvel-mar2020

description: Follow these steps to create a default phone number for callers to join a Microsoft Teams meeting.
---

# Set the phone numbers included on invites in Microsoft Teams

Audio Conferencing in Microsoft 365 and Office 365 enables users in your organization to create Microsoft Teams meetings, and then allow users to dial in to those meetings using a phone number.

A conferencing bridge gives you a set of dial-in phone numbers for your organization. All of them can be used to join the meetings that a meeting organizer creates, but you can select which ones are included on their meeting invites.

In addition to the meeting organizer's included phone numbers, each meeting invite also has a link at the bottom to access the full list of all available dial-in numbers.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Initial assignment of phone numbers that are included in the meeting invites for users

The phone numbers included in the meeting invites of users enabled for Audio Conferencing are defined in the **`-TeamsAudioConferencingPolicy`** that is assigned to users. When a user is assigned **`-TeamsAudioConferencingPolicy`**, all toll and toll-free phone numbers added in the policy are included in meeting invites for these users. If a user is assigned a **`-TeamsAudioConferencingPolicy`**  without any toll or toll-free numbers specified, their meeting invites display default conferencing numbers set in their individual settings.

> [!NOTE]
> Toll or toll-free phone numbers added to the *TeamsAudioConferencingPolicy* of a user take precedence over the phone numbers set individually using the default conferencing toll phone number and the default conferencing toll-free phone number in a user's settings.

As noted, in addition to phone numbers, each meeting invite contains a link that opens the full list of all dial-in phone numbers that can be used to join a given meeting.

> [!IMPORTANT]
> It can take up to 24 hours for the assigned phone numbers to show up on your meeting invite. If you aren't seeing updated numbers appear, please wait at least 24 hours before contacting support.

### New users

**`-TeamsAudioConferencingPolicy`** also defines the toll and toll-free phone numbers included in meeting invites for new users. By default, all new users are assigned the Global **`-TeamsAudioConferencingPolicy`**. The Global policy doesn't have any phone numbers added, unless an admin changes this. In this scenario, the meeting invites for users with Audio Conferencing enabled display default toll and toll-free conferencing numbers from each user's settings.

"For a new user, the default conferencing toll numbers are assigned based on their Usage Location set in the Microsoft 365 administration center when enabling the Audio Conferencing service. If there's a toll number in the conference bridge that matches the country/region of the user, that number is automatically assigned as the default toll number of the user. If there isn't one, the number defined as the default toll number of the conference bridge is assigned as the default toll number of the user.  

Once the user is enabled for the Audio Conferencing service, admin can change the default toll and toll-free phone numbers of the user from their initial values as needed.

To Set or change the default audio conferencing phone number for users in PowerShell using the **`-TeamsAudioConferencingPolicy`** cmdlet, see [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md).

## Set or change the default audio conferencing phone number for a meeting organizer or user individually

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Sign in to the Microsoft Teams admin center.

2. In the left navigation, select **Users**.

    ![Shows selecting users in the Microsoft Teams admin center.](media/Admin-users.png)

3. Select the user name from the list of available users.

4. Next to **Audio Conferencing**, select **Edit**.

    ![Click Edit next to Audio conferencing.](media/teams-set-phone-numbers-on-invites-image3.png)

5. Use the **Toll number** or **Toll-free number** fields to enter the numbers for the user.

> [!IMPORTANT]
> When you change a user's audio conferencing settings, recurring and future Microsoft Teams meetings must be updated and sent to attendees.

> [!NOTE]
> The phone numbers entered in this setting are only used if the *TeamsAudioConferencingPolicy* assigned to the user doesn't have any phone numbers added.

## Want to use Windows PowerShell

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 by using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these articles:

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

To set or change the default audio conferencing phone number for a meeting organizer or user using [Microsoft Teams PowerShell](/powershell/module/teams), set the **`ServiceNumber`** or **`TollFreeServiceNumber`** parameters of the [Set-CsOnlineDialInConferencingUser](/powershell/module/teams/set-CsOnlineDialInConferencingUser) cmdlet to one of the available numbers.

## Related topics

- [Try or purchase Audio Conferencing in Microsoft 365 for Microsoft Teams](try-or-purchase-audio-conferencing-in-office-365-for-teams.md)

- [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md)
