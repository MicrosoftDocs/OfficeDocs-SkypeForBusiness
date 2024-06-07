---
title: Prevent users from sharing content in external Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: maahma
ms.date: 5/22/2024
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Learn how to control whether users in your org with a Teams Premium license can share content when attending external Teams meetings.
appliesto: 
  - Microsoft Teams
---
# Prevent users from sharing content in external Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

## Overview

If you enabled content sharing for users in your org, they can present a screen, window, or app in Microsoft Teams meetings. When users from your org attend external meetings, they can share content if the organizer of that meeting set **Who can present** to **Everyone** or **Specific people**. However, you might want to prevent some of your users from sharing sensitive information when attending external meetings. As an admin, you can control whether users in your org with a Teams Premium license can share content when attending external Teams meetings.

## Manage the types of meetings your users can share content in

You can use the Teams admin center or the **`-ContentSharingInExternalMeetings`** parameter in PowerShell to manage the types of meetings your users can share content in.

|Teams admin center policy option|PowerShell value| Behavior |
|---------|---------|---------------|
|Any org | EnabledForAnyone |**This is the default value.** Users with this assigned policy can share content when attending meetings that any org hosts. |
|Trusted orgs and guests | EnabledForTrustedOrgs |Users with this assigned policy can only share content when attending meetings that trusted orgs and guests that you defined in your [External access policy](trusted-organizations-external-meetings-chat.md) host.|
|No other orgs | Disabled | Users with this assigned policy can’t share content when attending any external meetings.|

### Prevent users from sharing content in external meetings in the Teams admin center

Follow these steps in the Teams admin center to manage the types of meetings your users can share content in:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Content sharing** section.
6. Set **Participants can share content in external meetings hosted by** to your chosen value of either **Any org**, **Trusted orgs and guests**, or **No other orgs**.
7. Select **Save**

### Prevent users from sharing content in external meetings using PowerShell

You can use the **`-ContentSharingInExternalMeetings`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to manage which external meetings your users can share content in.

To prevent users with this policy from sharing content in any external meetings, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ContentSharingInExternalMeetings Disabled
```

For users with this policy to only share content in meetings that trusted orgs and guests host, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ContentSharingInExternalMeetings EnabledForTrustedOrgs
```

### Supported and unsupported meeting types and platforms

This feature supports the following meeting types and platforms:

- Meetings scheduled through Outlook and Teams calendar
- Desktop T2.1 (Windows and Mac)
- Mobile (Android and iOS)
- Web
- VDI 2.0
- Shared channel meetings
- Private or public channel meetings

This feature doesn’t support the following meeting types and platforms:

- [Microsoft Teams free meetings](https://www.microsoft.com/microsoft-teams/free)
- Meetings scheduled through Graph
- Group Calls/1:1 calls
- Meet now
- MTR [Windows, Surface Hub, Android], CVI, VDI 1.0
- Classic Teams
- TFL and TFW meeting federation

This policy doesn't prevent your users from sharing content in external meetings anonymously when they aren't signed into Teams.

## Related articles

- [Manage meeting policies for content sharing](meeting-policies-content-sharing.md)
- [Prevent users from joining external Microsoft Teams meetings](external-meeting-join.md)
- [Manage chat in Microsoft Teams meetings](manage-meeting-chat.md#manage-chat-messages-in-teams-meetings-hosted-by-other-organizations-that-you-dont-have-a-trusted-relationship-with)
