--- 
title: Manage chat in Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: heiris
ms.date: 10/12/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage meeting chat in Teams meetings and manage meeting chat in unfederated Teams meetings hosted by other organizations that you don’t have a trusted relationship with.
---

# Manage chat in Microsoft Teams meetings

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

## Overview

In Microsoft Teams, meeting chat allows participants to exchange messages to each other before, during, and after meetings. As an admin you can control:

- Whether participants in your users' meetings can read and write chat messages
- Whether users in your organization can use chat when they're participants in Teams meetings hosted by other organizations where there isn’t a trusted relationship.

For town halls, only presenters, organizers, and co-organizers can use chat with each other.

## Manage chat messages for your organization's Teams meetings

The **Meeting chat** setting controls whether participants in your users' meetings can and read and write chat messages. This setting doesn't apply to channel meetings and is a per-user and per-organizer policy.

In addition to this **Meeting chat** policy, your users have their own **Meeting chat** control in their meeting options.
As long as the admin policy isn't set to **Off for everyone**, meeting organizers can use this meeting option to manage the availability of chat in meetings they create. With this setting, organizers can control whether chat is **On**, **Off**, or **In meeting only** for their meetings. For more information on your end users' **Meeting chat**, see [Participant settings for a Teams meeting.](https://support.microsoft.com/office/participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e)

|Setting value |Behavior  |
|---------|---------|
|**On for everyone**     | All participants can read and write chat messages; the organizer's **Allow meeting chat** settings control the chat experience.|
|**On for everyone but anonymous users**     | All participants can read and write chat messages, except for anonymous participants. The organizer's **Allow meeting chat** settings control the chat experience for everyone, except for anonymous participants, who can't read or write any messages. |
|**Off for everyone**     | Meeting chat is turned off for all participants; organizers can't use their **Allow meeting chat** to turn on chat in their meetings.  |

### Manage meeting chat for your organization's Teams meetings using the Teams admin center

You can manage meeting chat for your users in the Teams admin center.

Use these steps to manage meeting chat:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy you'd like to edit.
1. Navigate to the **Meeting engagement** section.
1. Set **Meeting chat** to your chosen value of either  **On for everyone**, **On for everyone but anonymous users**, or  **Off for everyone**.
1. Select **Save**.

### Manage meeting chat using PowerShell

You can manage meeting chat for your users by using the following PowerShell cmdlets in Teams PowerShell:

- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)

The **`-MeetingChatEnabledType`** parameter controls the availability of meeting chat with the following settings:

- **Enabled** to be **"On for everyone"**
- **EnabledExceptAnonymous** to be **"On for everyone but anonymous users"**
- **Disabled** to be **"Off for everyone"**

To allow meeting chat to be on for everyone with this assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType Enabled
```

To allow meeting chat to be on for everyone but anonymous users with this assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType EnabledExceptAnonymous
```

To disable meeting chat for everyone with this assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -MeetingChatEnabledType Disabled
```

To learn more about chat for your end users, see [Chat in a Teams meeting](https://support.microsoft.com/office/64e2cb91-8a11-4781-94ea-fbb23f2b922f).

## Manage chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with

The **Chat in external meetings** setting controls whether users in your organization can use chat when they're participants in Teams meetings hosted by other organizations where there isn’t a trusted relationship configured in [external access](trusted-organizations-external-meetings-chat.md). (In such a case, your users are considered anonymous by the other organization.) This setting is a per-user and per-participant policy.

|Setting value |Behavior  |
|---------|---------|
|**On**  | **This is the default value.** Users in your organization can read and write meeting chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with. You must also set [**Meeting chat**](manage-meeting-chat.md) to **On for everyone** and the meeting organizer must set [**Allow meeting chat**](https://support.microsoft.com/office/participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e) to either **Enabled** or **In meeting only**. |
|**Off** | Users in your organization can't read or write meeting chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with.  |

Use the Teams admin center or PowerShell to manage whether users in your organization can use chat messages in Teams meetings hosted by other organizations.

### Manage chat in meetings hosted by other organizations using the Teams admin center

If you'd like to choose whether users in your organization can use chat in Teams meetings hosted by other organizations, follow these steps:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
2. Select the policy you'd like to edit, or create a new one.
3. Navigate to the **Meeting engagement** section.
4. Toggle **External meeting chat** to **On** or **Off**.
5. Select **Save**.

### Manage chat in meetings hosted by other organizations using PowerShell

You can manage chat in Teams meetings hosted by other organizations by using the following PowerShell cmdlets in Teams PowerShell:

- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)

The **`-AllowExternalNonTrustedMeetingChat`** parameter controls the availability of meeting chat for your users when they attend external meetings.  This parameter uses the following settings:

- **True**
- **False**

To disable chat in Teams meetings hosted by other organizations for users with the assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalNonTrustedMeetingChat $False
```

To enable chat in Teams meetings hosted by other organizations for users with the assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalNonTrustedMeetingChat $True 
```

## Related topics

[Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)

[Teams policy reference](settings-policies-reference.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)
