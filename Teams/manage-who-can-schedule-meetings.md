---
title: Manage who can start instant meetings and schedule meetings
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: nej, brgussin
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use Teams meeting policy settings to control who can start instant meetings and schedule meetings.
---

# Manage who can start instant meetings and schedule meetings

As an admin, you can restrict which users can start instant meetings and schedule meetings in Teams. This can be especially useful for privacy and security reasons, where you may not want particular users setting up meetings.

The meeting policy settings are turned on by default. These settings can be found in the Teams admin center under **Meetings** > **Meeting policies**.

- **Meet now in channels**: Controls whether a user can start an instant meeting in a channel.
- **Channel meeting scheduling**: Controls whether a user can schedule a meeting in a channel.
- **Private meeting scheduling**: Controls whether a user can schedule a private meeting in Teams. A meeting is private when it's not published to a channel in a team.
- **Outlook add in**: Controls whether a user can schedule a private meeting from Outlook. A meeting is private when it's not published to a channel in a team.
- **Meet now in private meetings**: Controls whether a user can start an instant private meeting.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Channel meetings

If you have compliance requirements that mandate only specific people start instant channel meetings and schedule channel meetings, then you can create or update your meeting policy to restrict these settings. You can then create a separate policy attributed to users who you want to start instant channel meetings and schedule channel meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **General**, toggle the following:
    1. If you want to restrict who can start instant meetings in a channel, toggle **Meet now in channels** to **Off**.
    1. If you want to restrict who can schedule meetings in a channel, toggle **Channel meeting scheduling** to **Off**.
1. Hit **Save** at the bottom of the page.

## Private meetings

If you have compliance requirements that mandate only specific people start instant private meetings and schedule private meetings, then you can create or update your meeting policies to restrict these settings. You can then create a separate policy attributed to users who you want to start instant meetings and schedule private meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **General**, toggle the following:
    1. If you want to restrict who can start instant private meetings, toggle **Meet now in private meetings** to **Off**.
    1. If you want to restrict who can schedule private meetings in a channel, toggle **Private meeting scheduling** to **Off**.
1. Hit **Save** at the bottom of the page.

## Turning off meeting policy settings

After any of these meeting policy settings are turned off, any user assigned to the policy will not be able to start or schedule meetings of that type. The meeting join links and conference IDs of all existing meetings of that type that the user had previously started or scheduled will not work. When a user tries to join the meeting through an inactive join link or by phone, they'll get a message that says the meeting is no longer available.

For example, if a user is assigned a meeting policy in which these meeting policy settings are set to **On**, and then you turn off the **Allow Meet now in channels** setting, that user can no longer start instant meetings in channels, and the Meet now join links that the user previously created won't work. However, the user can still start and schedule other meeting types and join meetings organized by other people.

Even if a meeting policy is turned off, the conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.

If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled meetings organized by the user become active and people can join them using the meeting join link or by phone.

## Related topics

[Change meeting expiration date - end-user controls](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24#bkmk_view_change_expiration_date)

[Manage meeting policies in Teams](meeting-policies-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)

[Limits and specifications for Microsoft Teams](/microsoftteams/limits-specifications-teams)
