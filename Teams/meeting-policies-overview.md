---
title: Manage meeting policies in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
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
  - ms.teamsadmincenter.meetingpolicies.overview
  - seo-marvel-apr2020
description: Learn to manage meeting policy settings in Teams and use them to control the features available to meeting participants for meetings scheduled by users.
---
# Manage meeting policies in Microsoft Teams

<a name="bkautomatically-admit-people"> </a>

<a name="bkallow-a-participant-to-give-or-request-control"> </a>

<a name="bkallow-transcription"> </a>

Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. You can use the global (Org-wide default) policy that's automatically created or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using [PowerShell](teams-powershell-overview.md).

> [!NOTE]
> For information about using roles to manage the permissions of meeting presenters and attendees, see [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019?ui=en-us&rs=en-us&ad=us).

You can implement policies in the following ways, which affect the meeting experience for users before a meeting starts, during a meeting, or after a meeting.

|Implementation type  |Description  |
|---------|---------|
|Per-organizer    |When you implement a per-organizer policy, all meeting participants inherit the policy of the organizer. For example, **Automatically admit people** is a per-organizer policy and controls whether users join the meeting directly or wait in the lobby for meetings scheduled by the user who is assigned the policy.          |
|Per-user    |When you implement a per-user policy, only the per-user policy applies to restrict certain features for the organizer and/or meeting participants. For example, **Meet now in channels** is a per-user policy.     |
|Per-organizer and per-user     |When you implement a combination of a per-organizer and per-user policy, certain features are restricted for meeting participants based on their policy and the organizer's policy. For example, **Cloud recording** is a per-organizer and per-user policy. Turn on this setting to allow the meeting organizer and participants to start and stop a recording.

You can edit the settings in the global policy or create and assign one or more custom policies. Users will get the global policy unless you create and assign a custom policy.

> [!NOTE]
> Meeting details button will be available if a user has the audio conference licenses enabled or the user is allow for audio conferencing, if not, the meeting details will not be available.

## Create a custom meeting policy

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies**.
2. Click **Add**.
3. Enter a name and description for the policy. The name can't contain special characters or be longer than 64 characters.
4. Choose the settings that you want.
5. Click **Save**.

For example, say you have a bunch of users and you want to limit the amount of bandwidth that their meeting would require. You would create a new custom policy named "Limited bandwidth" and disable the following settings:

Under **Audio & video**:

- Turn off Cloud recording.
- Turn off IP video.

Under **Content sharing**:

- Disable screen sharing mode.
- Turn off Whiteboard.
- Turn off Shared notes.

Then assign the policy to the users.

The following video shows the steps described in this section.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE53Wv0?autoplay=false]

## Edit a meeting policy

You can edit the global policy and any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. From here, make the changes that you want.
4. Click **Save**.

> [!NOTE]
> A user can be assigned only one meeting policy at a time.

## Assign a meeting policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

> [!NOTE]
> You can't delete a policy if users are assigned to it. You must first assign a different policy to all affected users, and then you can delete the original policy.

## Meeting policy settings

When you select an existing policy on the **Meeting policies** page or select **Add** to add a new policy, you can configure settings for the following.

- [General](meeting-policies-in-teams-general.md)
- [Audio & video](meeting-policies-audio-and-video.md)
- [Recording & transcription](meetings-policies-recording-and-transcription.md)
- [Content sharing](meeting-policies-content-sharing.md)
- [Participants & guests](meeting-policies-participants-and-guests.md)

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
