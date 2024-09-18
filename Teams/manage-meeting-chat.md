--- 
title: Manage chat in Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: heiris
ms.date: 9/18/2024
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

In Microsoft Teams, chat allows participants to exchange messages to each other before, during, and after meetings and webinars. For town halls, only presenters, organizers, and co-organizers can use chat with each other. As an admin you can control:

- Whether participants in your users' meetings and webinars can read and write chat messages.
- Whether users in your organization can use chat when they're participants in Teams meetings hosted by other organizations where there isn’t a trusted relationship.

## Manage chat messages for your organization's Teams meetings

The **Meeting chat** setting controls whether participants in your users' meetings can and read and write chat messages. This setting doesn't apply to channel meetings and is a per-user and per-organizer policy.

In addition to this **Meeting chat** policy, your users have their own **Meeting chat** control in their meeting options. If the admin policy isn't set to **Off for everyone**, organizers can manage chat availability in their meetings and webinars. They can choose to set chat to **On**, **Off**, or **In meeting only**. For more information on your users' **Meeting chat** controls, see [Chat in a Teams meeting](https://support.microsoft.com/office/64e2cb91-8a11-4781-94ea-fbb23f2b922f).

The following table describes the behavior for your **Meeting chat** policy settings:

|Setting value |PowerShell value|Behavior |
|---------|---------|---------|
|**On for everyone**  | Enabled|All participants can read and write chat messages; the organizer's **Allow meeting chat** settings control the chat experience. Organizers can also manage chat availability in their meetings and webinars.|
|**On for everyone but anonymous users**  | EnabledExceptAnonymous|All participants can read and write chat messages, except for anonymous participants. The organizer's **Allow meeting chat** settings control the chat experience for everyone, except for anonymous participants, who can't read or write any messages. Organizers can also manage chat availability in their meetings and webinars.|
|**Off for everyone**  | Disabled| Meeting chat is turned off for all participants; organizers can't use their **Allow meeting chat** to turn on chat in their meetings. Organizers can't manage chat availability in their meetings and webinars. |

### Manage meeting chat for your organization's Teams meetings using the Teams admin center

To manage meeting chat for your users in the Teams admin center, use the following steps:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy you'd like to edit.
1. Navigate to the **Meeting engagement** section.
1. Set **Meeting chat** to your chosen value of either **On for everyone**, **On for everyone but anonymous users**, or **Off for everyone**.
1. Select **Save**

### Manage meeting chat using PowerShell

You can use the **`-MeetingChatEnabledType`** parameter in the[Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to control the availability of meeting chat.

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

The **Chat in external meetings** setting determines if users in your organization can chat in Teams meetings hosted by other organizations without a trusted relationship configured in [external access](trusted-organizations-external-meetings-chat.md). In such cases, the other organization considers your users to be anonymous. This setting is a per-user and per-participant policy.

The following table describes the behavior for your **Chat in external meetings** policy settings:

|Teams admin center value | PowerShell value| Behavior |
|---------|---------|---------|
|**On** | True|**This is the default value.** Users in your organization can read and write meeting chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with. You must also set [**Meeting chat**](#manage-chat-messages-for-your-organizations-teams-meetings) to **On for everyone** and the meeting organizer must set [**Allow meeting chat**](https://support.microsoft.com/office/participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e) to either **Enabled** or **In meeting only**. |
|**Off** | False|Users in your organization can't read or write meeting chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with. |

You can use the Teams admin center or PowerShell to manage whether users in your organization can use chat messages in Teams meetings hosted by other organizations without a trusted relationship.

### Manage chat in meetings hosted by other organizations using the Teams admin center

If you'd like to choose whether users in your organization can use chat in Teams meetings hosted by other organizations, follow these steps:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
2. Select the policy you'd like to edit, or create a new one.
3. Navigate to the **Meeting engagement** section.
4. Toggle **External meeting chat** to **On** or **Off**.
5. Select **Save**.

### Manage chat in meetings hosted by other organizations using PowerShell

The **`-AllowExternalNonTrustedMeetingChat`** parameter in the[Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet controls the availability of meeting chat for your users when they attend external meetings. 

To disable chat in Teams meetings hosted by other organizations for users with the assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalNonTrustedMeetingChat $False
```

To enable chat in Teams meetings hosted by other organizations for users with the assigned policy, run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalNonTrustedMeetingChat $True 
```

## Related topics

- [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)
- [Teams policy reference](settings-policies-reference.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)
