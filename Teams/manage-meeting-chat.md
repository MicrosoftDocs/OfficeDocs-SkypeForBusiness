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

The **Meeting chat** setting controls whether meeting chat is allowed in the user's meeting. This setting doesn't apply to channel meetings. This is a per-user and per-organizer policy.

|Setting value |Behavior  |
|---------|---------|
|**On for everyone**     | All participants can write and view chat messages. |
|**Off for everyone**     | Meeting chat is turned off for all participants.  |
|**On for everyone but anonymous users**     | Meeting chat write access is turned off for anonymous participants only.  |

To configure meeting chat
1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Meeting engagement** section.
1. Set **Meeting chat** to one of the values described above.
1. Select **Save**.

Once this **Chat in meetings** policy is applied to users, an organizer can't override this policy through **Meeting options**.

The policy applied to the meeting organizer can affect other users in the meeting. For example:

- If the organizer has **Chat in meetings** set to **On for everyone** or **On for everyone but anonymous users**, then a user's individual policy will apply and any users with **On for everyone** set won't be able to chat in the meeting.
- If the organizer has **Chat in meetings** set to **Off for everyone**, the organizer's policy applies and no one will be able to chat in the meeting.

Information about chat for your end users can be found in [Chat in a Teams meeting](https://support.microsoft.com/office/64e2cb91-8a11-4781-94ea-fbb23f2b922f).

## Related topics

[Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)

[Teams policy reference](settings-policies-reference.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)
