---
title: Manage meeting and event policies in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: bryannyce
ms.date: 8/14/2024
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.overview
  - seo-marvel-apr2020
description: Learn to manage meeting and event policy settings in Teams and use them to control the features available to meeting participants for meetings, webinars, and town halls.
---
# Manage meeting and event policies in Microsoft Teams

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

As an admin, you can use meeting and event policies to control the features that are available to organizers and participants of meetings, webinars, and town halls in your organization. Depending on the feature, you can manage meeting policies in the Microsoft Teams admin center or through [PowerShell](teams-powershell-overview.md).

You can edit the settings in the global policy or create and assign one or more custom policies. Users get the global policy unless you create and assign a custom policy.

Policies are implemented in one of the following ways:

|Implementation type  |Description  |
|---------|---------|
|Per-organizer    |When you implement a per-organizer policy, all participants inherit the policy of the organizer. For example, **Who can bypass the lobby** is a per-organizer policy and controls whether users join the meeting directly or wait in the lobby for meetings scheduled by the user who is assigned the policy.|
|Per-user    |When you implement a per-user policy, the policy allows or prevents a given feature for each user. For example, **Meet now in channel meetings** is a per-user policy.     |
|Per-organizer and per-user     |When you implement a combination of a per-organizer and per-user policy, certain features are restricted for participants based on their policy and the organizer's policy. For example, **Meeting recording** is a per-organizer and per-user policy. Turn on this setting to allow the meeting organizer and participants to start and stop a recording.|

## Create a custom meeting or event policy

1. In the left navigation of the Teams admin center, go to **Meetings** > **Meeting policies** or **Event policies**.
2. Select **Add**.
3. Enter a name and description for the policy. The name can't contain special characters or be longer than 64 characters.
4. Choose the settings that you want.
5. Select **Save**.

> [!NOTE]
> Policy name can't be changed once a policy has been created.

This video shows the steps to create and assign a custom meeting policy to a user (or users).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1c7DS?autoplay=false]

## Edit a meeting or event policy

You can edit the global policy and any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies** or **Event policies**.
2. Choose the policy by clicking to the left of the policy name, and then select **Edit**.
3. From here, make the changes that you want.
4. Select **Save**.

> [!NOTE]
> A user can be assigned only one meeting policy and one event policy at a time.

This video shows the steps to edit an organizational-wide default meeting policy.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1ca7L?autoplay=false]

## Assign a meeting or event policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

> [!NOTE]
> You can't delete a policy if users are assigned to it. You must first assign a different policy to all affected users, and then you can delete the original policy.

## Related topics

- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019)
