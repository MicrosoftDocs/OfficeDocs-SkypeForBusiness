---
title: Manage chat for sensitive Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 09/28/2022
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn how to manage Teams meeting chat options for sensitive meetings by using admin policies, sensitivity labels, and meeting templates.
---

# Manage chat for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

By default, all meeting attendees can chat both during and after the meeting. Meeting organizers can turn this feature off or allow chat only during the meeting.

If you have compliance requirements for certain types of meetings, you can manage how and when chat is enabled by using a combination of Teams admin policies, meeting templates, and sensitivity labels.

The following table show what chat-related controls are available and where they can be managed.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Meeting chat|Yes|Yes|Yes|Yes|
|Prevent copying chat content to clipboard|No|Yes|No|No|
|Q&A|Yes|No|No|Yes|
|Shared notes|Yes|No|No|No|

> [!Note]
> Meeting settings in sensitivity labels and custom meeting templates require Teams Premium.

By default, chat is turned on for meeting participants. There are several ways you can manage chat:

- Prevent anonymous meeting participants from using chat
- Prevent the meeting chat from being used before or after the meeting
- Preventing copying of chat contents
- Turn the chat off entirely

If you want to prevent anonymous meeting participants from using chat, you can configure the **Chat in meetings** Teams admin policy to exclude them. This setting can't be configured by meeting organizers or by using a meeting template or sensitivity label.

Meeting organizers can specify that the chat only be available while the meeting is in progress. This can also be configured by using a meeting template or sensitivity label if you require this for certain types of meetings.

You can prevent copying of chat contents by using a sensitivity label. Note that if a sensitivity label that restricts copying from the chat is specified as the default channel label in a container label, then teams with that container label will restrict copying from the chat for all channels in the team, both in and out of channel meetings.

## Options for meetings without chat

Some organizations require that meeting chat be turned off entirely for certain types of meetings. For example, an organization that holds meetings where personal data is discussed might want to turn off the meeting chat because of the regulatory requirements around storing this information.

For meetings where sensitive or highly sensitive information is shared and you want to turn off the meeting chat, you can enforce this by using a meeting template or sensitivity label.

In meetings where the chat is not available, meeting organizers can turn on the [Q&A feature](https://support.microsoft.com/office/f3c84c72-57c3-4b6d-aea5-67b11face787). This allows attendees to ask questions or comment in writing. This feature is available but off by default for meeting organizers. Teams administrators can prevent meeting organizers from using it by turning off the **Q&A** admin meeting policy.

By default, Teams also allows meeting attendees to [create shared meeting notes](https://support.microsoft.com/office/3eadf032-0ef8-4d60-9e21-0691d317d103) and use the [whiteboard](https://support.microsoft.com/whiteboard). While the meeting organizer can't turn these features off, you can turn them off for people and groups by using the **Shared notes** and **Whiteboard** admin meeting policies in the Teams admin center.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)

[Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md)

[Manage retention policies for Microsoft Teams](retention-policies.md)
