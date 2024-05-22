---
title: Prevent users from sharing content in external Teams meetings
ms.author: wlibebe
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
description: Learn how to manage the registration form for webinars in Microsoft Teams for admins. You can manage default questions, custom questions, and predefined questions.
appliesto: 
  - Microsoft Teams
---
# Prevent users from sharing content in external Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

## Overview

If you enabled content sharing for users in your org, they can present a screen, window, or app in Microsoft Teams meetings. When users from your organization attend external meetings, they can share content if the organizer of that meeting set Who can present to Everyone or Specific People. However, you might want to prevent some users from sharing content in external meetings. As an admin, you can control whether users in your org with a Teams Premium license can share content when attending external Teams meetings.

To learn more about content sharing policies, see [Manage meeting policies for content sharing](meeting-policies-content-sharing.md).

To prevent your users from joining external Teams meetings, see [Prevent users from joining external Microsoft Teams meetings](external-meeting-join.md).

To manage chat for your users in external meetings, see [Manage chat in Teams meetings](manage-meeting-chat.md#manage-chat-messages-in-teams-meetings-hosted-by-other-organizations-that-you-dont-have-a-trusted-relationship-with).

The following table describes how different roles in Teams interact with this policy:

|User role| Policy effect|
|---------|---------------|
|Trusted org participants and guests| When this policy is set to **Anyone** or **or Only people in trusted orgs and guests**, these users in your org can share content in meetings that trusted organizations (as defined in External access) host. When set to **Specific orgs**, users can share content in meetings that organizations you choose in this policy host.<br><br> When this policy is set to No other orgs, these users in your org can't share content in externally hosted Teams meetings while using your org’s accounts. However, your users can still share content in external meetings as anonymous if they aren’t logged in to Teams.|
|Anonymous| This policy doesn't prevent users from sharing content in external meetings anonymously if they’re not signed into Teams.|

### Supported and unsupported meeting types

This feature doesn’t support the following meeting types:

- [Microsoft Teams free meetings](https://www.microsoft.com/microsoft-teams/free)

This feature supports the following meeting types:

- Shared Channel meetings
- Private or Public channel meetings
- Meetings scheduled through Graph
- Group Calls/1:1 calls
- Meet now

## Manage the types of meetings your users can share content in

You can use the Teams admin center or the **`-ContentSharingInExternalMeetings`** parameter in PowerShell to manage the types of meetings your users can share content in.

|Teams admin center policy option|PowerShell value| Behavior |
|---------|---------|---------------|
|Any org | EnabledForAnyone |**This is the default value.** Users with this assigned policy can share content when attending meetings that any org hosts. |
|Trusted orgs and guests | EnabledForTrustedOrgs |Users with this assigned policy can only share content when attending meetings that trusted orgs and guests(defined in your External access policy) host.|
|Specific orgs | | Users with this assigned policy can only share content when attending meetings that specific orgs you choose in this policy host.|
|No other orgs | Disabled | Users with this assigned policy can’t share content when attending any external meetings.|

### Prevent users from sharing content in external meetings in the Teams admin center

Follow these steps in the Teams admin center to manage the types of meetings your users can share content in:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Content sharing** section.
6. Set **Participants can share content in external meetings hosted by** to your chosen value of either **Any org**, **Trusted orgs and guests**, **Specific orgs**, or **No other orgs**.

      - 1. If you select **Specific orgs**, select the **Add Domains** button to open a panel. In the panel, enter the domain names for orgs that can host meetings where users with this policy are allowed to share content in. This policy takes precedence over your [external access policies](trusted-organizations-external-meetings-chat.md).
      - 2. After you enter the domain name, select the **‘Add *[domain name]* as a domain** dropdown.
      - 3. Select **Done**
7. Select **Save**

### Prevent users from sharing content in external meetings using PowerShell

You can use PowerShell to manage the types of questions an organizer can require attendees to answer when registering for webinars. To manage the registration form questions, use the **`-ContentSharingInExternalMeetings`** parameter in the **CsTeamsEventsPolicy** cmdlet.

To prevent users with this policy from sharing content in any external meetings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -ContentSharingInExternalMeetings Disabled
```

For users with this policy to only share content in meetings that trusted orgs and guests host, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -ContentSharingInExternalMeetings EnabledForTrustedOrgs
```

## Related articles

- [Manage meeting policies for content sharing](meeting-policies-content-sharing.md)
- [Prevent users from joining external Microsoft Teams meetings](external-meeting-join.md)
- [Manage chat in Teams meetings](manage-meeting-chat.md#manage-chat-messages-in-teams-meetings-hosted-by-other-organizations-that-you-dont-have-a-trusted-relationship-with)
