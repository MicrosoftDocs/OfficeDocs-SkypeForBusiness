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

The **Meeting chat** setting controls whether meeting chat is allowed in the user's meeting. This setting doesn't apply to channel meetings. This is a per-user and per-organizer policy.

|Setting value |Behavior  |
|---------|---------|
|**On for everyone**     | All participants can write and view chat messages. |
|**On for everyone but anonymous users**     | Meeting chat read and write access is turned off for anonymous participants only.  |
|**Off for everyone**     | Meeting chat is turned off for all participants.  |

**THE BELOW IS THE OLD VERSION:**

To configure meeting chat:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Meeting engagement** section.
1. Set **Meeting chat** to one of the values described above.
1. Select **Save**.

Once this **Chat in meetings** policy is applied to users, an organizer can't override this policy through **Meeting options**.

The policy applied to the meeting organizer can affect other users in the meeting. For example:

- If the organizer has **Chat in meetings** set to **On for everyone** or **On for everyone but anonymous users**, then a user's individual policy will apply and any users with **On for everyone** set won't be able to chat in the meeting.
- If the organizer has **Chat in meetings** set to **Off for everyone**, the organizer's policy applies and no one will be able to chat in the meeting.

**NEW VERSION BELOW**:

In addition to this **Meeting chat** policy, your users have their own meeting option called **Allow meeting chat**. Organizers can use this meeting option to manage chat availability in meetings they create. For more information on **Allow meeting chat**, see [Participant settings for a Teams meeting.](https://support.microsoft.com/office/participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e)

The following table shows how an admin's **Meeting chat** policy settings will interact with an organizer's **Allow meeting chat** settings.

| Meeting chat | Allow meeting chat| Chat behavior for users|
|     :---:      |         :---:  |         :---:  |
| On for everyone   | Enabled | Participants and organizers can read and send messages before and during meetings. **Anonymous** users can read and send messages **during** meetings only.|
| On for everyone    | In meeting only | **Organizers** can send messages before and after the meeting, but **participants** can **only** read these messages. **During** the meeting, all participants can read and send messages.|
| On for everyone     | Disabled | **No one** can send messages before, during, or after meetings.|
| On for everyone but anonymous users   | Enabled | Participants and organizers can read and send messages before, during, and after meetings. However, **Anonymous** users **can’t** read or send any messages before, during, or after the meeting.|
| On for everyone but anonymous users     | In meeting only | **Anonymous** users **can’t** read or send any messages before, during, or after the meeting. **Organizers** can send messages before and after the meeting, but **participants** (excluding anonymous users)can **only** read these messages. **During** the meeting, participants can read and write messages.|
| On for everyone but anonymous users     | Disabled | **No one** can send messages before, during, or after meetings.|
| Off for everyone   | Enabled | **No one** can send messages before, during, or after meetings|
| Off for everyone    | In meeting only | **No one** can send messages before, during, or after meetings.|
| Off for everyone     | Disabled | **No one** can send messages before, during, or after meetings.|

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

- Placeholder text for cmdlet links.

The **`-MeetingChatEnabledType`** parameter controls the availability of meeting chat with the following settings:

- **Enabled** to be **"On for everyone"**
- **EnabledExceptAnonymous** to be **"On for everyone but anonymous users"**
- **Disabled** to be **"Off for everyone"**

The following example sets meeting chat to be on for everyone:
**THE BELOW IS PLACEHOLDER TEXT**

```PowerShell
-MeetingChatEnabledType <String>
```


Information about chat for your end users can be found in [Chat in a Teams meeting](https://support.microsoft.com/office/64e2cb91-8a11-4781-94ea-fbb23f2b922f).

## Related topics

[Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)

[Teams policy reference](settings-policies-reference.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)
