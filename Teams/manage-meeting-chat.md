--- 
title: Manage chat in Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
ms.date: 04/13/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage meeting chat in Teams meetings.
---

# Manage chat in Teams meetings

## Overview

The **Meeting chat** setting controls whether participants in your users' meetings can and read and write chat messages. This setting doesn't apply to channel meetings and is a per-user and per-organizer policy.

In addition to this **Meeting chat** policy, your users have their own meeting option called **Allow meeting chat**.
As long as the admin policy isn't set to **Off for everyone**, meeting organizers can use this meeting option to manage the availability of chat in meetings they create. With this setting, organizers can control whether chat is **Enabled**, **Disabled**, or **In meeting only** for their meetings. For more information on **Allow meeting chat**, see [Participant settings for a Teams meeting.](https://support.microsoft.com/office/participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e)

|Setting value |Behavior  |
|---------|---------|
|**On for everyone**     | All participants can read and write chat messages; the organizer's **Allow meeting chat** settings control the chat experience.|
|**On for everyone but anonymous users**     | All participants can read and write chat messages, except for anonymous participants. The organizer's **Allow meeting chat** settings control the chat experience for everyone, except for anonymous participants, who can't read or write any messages. |
|**Off for everyone**     | Meeting chat is turned off for all participants; organizers can't use their **Allow meeting chat** to turn on chat in their meetings.  |

## Manage meeting chat using the Teams admin center

You can manage meeting chat for your users in the Teams admin center.

Use these steps to manage meeting chat:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy you'd like to edit.
1. Navigate to the **Meeting engagement** section.
1. Set **Meeting chat** to your chosen value of either  **On for everyone**, **On for everyone but anonymous users**, or  **Off for everyone**.
1. Select **Save**.

## Manage meeting chat using PowerShell

You can manage meeting chat for your users by using the following PowerShell cmdlets in Teams PowerShell:

- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/skype/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/skype/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/skype/remove-csteamsmeetingpolicy)

The **`-MeetingChatEnabledType`** parameter controls the availability of meeting chat with the following settings:

- **Enabled** to be **"On for everyone"**
- **EnabledExceptAnonymous** to be **"On for everyone but anonymous users"**
- **Disabled** to be **"Off for everyone"**

To allow meeting chat to be on for everyone with an assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType Enabled
```

To allow meeting chat to be on for everyone but anonymous users with an assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType EnabledExceptAnonymous
```

To disable meeting chat for everyone with an assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType Disabled
```

Information about chat for your end users can be found in [Chat in a Teams meeting](https://support.microsoft.com/office/64e2cb91-8a11-4781-94ea-fbb23f2b922f).

## Related topics

[Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)

[Teams policy reference](settings-policies-reference.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)
