---
title: Manage chat for sensitive Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
appliesto: 
  - Microsoft Teams
description: Learn how to manage Teams meeting chat options for sensitive meetings by using admin policies, sensitivity labels, and meeting templates.
---

# Manage chat for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

By default, all meeting attendees can chat both during and after the meeting. Meeting organizers can turn this feature off or allow chat only during the meeting.

If you have compliance requirements for certain types of meetings, you can manage how and when chat is enabled by using a combination of Teams admin policies, meeting templates, and sensitivity labels.

The following table show what chat-related controls are available and where they can be managed.

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:---------------:|:------:|:---------------:|:---------:|
|Attendees can chat|Yes|Yes|Yes|Yes|
|Meeting chat copy and paste|No|No|Yes|No|
|Meeting Q&A|Yes|No|No|Yes|
|Shared notes|No|No|No|Yes|

> [!Note]
> Meeting settings in sensitivity labels and custom meeting templates are in preview and will require a Teams Premium license.

By default, chat is turned on for meeting participants. There are several ways you can mange chat:

- Prevent anonymous meeting participants from using chat
- Prevent the meeting chat from being used before or after the meeting
- Preventing copy and paste of chat contents
- Turn the chat off entirely

If you want to prevent anonymous meeting participants from using chat, you can configure the **Chat in meetings** Teams admin policy to exclude them. This setting can't be configured by meeting organizers or by using a meeting template or sensitivity label.

Meeting organizers can specify that the chat only be available while the meeting is in progress. This can also be configured by using a meeting template or sensitivity label if you require this for certain types of meetings.

## Options for meetings without chat

Some organizations require that meeting chat be turned off entirely for certain types of meetings. For example, an organization that holds meetings where personally identifiable information (PII) is discussed might want to turn off the meeting chat because of the regulatory requirements around storing this information.

For meetings where sensitive or highly sensitive information is shared and you want to turn off the meeting chat, you can enforce this by using a meeting template or sensitivity label.

In meetings where the chat is not available, meeting organizers can turn on the [Q&A feature](https://support.microsoft.com/office/f3c84c72-57c3-4b6d-aea5-67b11face787). This allows attendees to ask questions or comment in writing. This feature is available but off by default for meeting organizers. Teams administrators can prevent meeting organizers from using it by turning off the **Teams Q&A** admin meeting policy.

By default, Teams also allows meeting attendees to [create shared meeting notes](https://support.microsoft.com/office/3eadf032-0ef8-4d60-9e21-0691d317d103) and use the [whiteboard](https://support.microsoft.com/whiteboard). While the meeting organizer can't turn these features off, you can turn them off for people and groups by using the **Shared notes** and **Whiteboard** admin meeting policies in the Teams admin center.

## Related topics

