---
title: Manage chat for sensitive Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: yilin.yang
ms.date: 01/22/2024
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

By default, all meeting attendees can chat both during and after a meeting. Meeting organizers can turn meeting chat off or allow chat only during the meeting.

If you have compliance requirements for certain types of meetings, you can manage how and when chat is enabled by using a combination of Teams admin policies, meeting templates, and sensitivity labels. You can also prevent copying chat content to the clipboard.

> [!NOTE]
> Meeting options in sensitivity labels and custom meeting templates require Teams Premium.

The following table show what chat-related controls are available and where they can be managed.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Meeting chat|Yes|Yes|Yes|Yes|
|Prevent copying chat content to clipboard|No*|Yes|Yes|Yes|
|Q&A|Yes|No|Yes|Yes|

*Teams admin policy can be used to allow or prevent meeting organizers from using the *prevent copying chat content to clipboard* feature, but can't enforce the use of the feature.

By default, chat is turned on for meeting participants. There are several ways you can manage chat:

- Prevent anonymous meeting participants from using chat
- Prevent the meeting chat from being used before or after the meeting
- Preventing copying of chat contents
- Turn the chat off entirely

If you want to prevent anonymous meeting participants from using chat, you can configure the **Chat in meetings** Teams admin policy to exclude them. This setting can't be configured by meeting organizers or by using a meeting template or sensitivity label.

Meeting organizers can specify that the chat only be available while the meeting is in progress. This can also be configured by using a meeting template or sensitivity label if you require this for certain types of meetings.

## Prevent copying or forwarding of chat

> [!IMPORTANT]
> Prevent copying or forwarding of chat on mobile clients is only supported through sensitivity labels.

You can prevent copying or forwarding of chat contents by using a meeting template or sensitivity label. If this option is not enforced by a template or sensitivity label, meeting organizers can control this feature in meeting options.

If you want to ensure that meeting participants can copy or forward meeting chat messages, you can use a Teams admin policy to disable the setting in meeting options and templates. Meeting organizers who have the policy assigned won't be able to prevent copying chat content to the clipboard in meetings they organize.

To ensure that participants can copy or forward meeting chat content, use the following steps:

1. In the Teams admin center, expand **Meetings**, and then select **Meeting policies**.
1. Choose the policy that you want to update, or create a new one.
1. In the **Content sharing** section, set **Organizer can restrict participants from copying or forwarding meeting chat messages** to **Off**
1. Select **Save**.

Note that meetings with a sensitivity label that prevents copying chat content to the clipboard overrides the Teams admin policy.

> [!NOTE]
> If a sensitivity label that restricts copying from the chat is specified as the default channel label in a container label, then teams with that container label will restrict copying from the chat for all channels in the team, both in and out of channel meetings.

## Options for meetings without chat

Some organizations require that meeting chat be turned off entirely for certain types of meetings. For example, an organization that holds meetings where personal data is discussed might want to turn off the meeting chat because of the regulatory requirements around storing this information.

For meetings where sensitive or highly sensitive information is shared and you want to turn off the meeting chat, you can enforce this by using a meeting template or sensitivity label.

In meetings where the chat isn't available, meeting organizers can turn on the [Q&A feature](https://support.microsoft.com/office/f3c84c72-57c3-4b6d-aea5-67b11face787). This allows attendees to ask questions or comment in writing. This feature is available but off by default for meeting organizers. Teams administrators can prevent meeting organizers from using it by turning off the **Q&A** admin meeting policy or disabling it in a meeting template.

By default, Teams also allows meeting attendees to [create shared meeting notes](https://support.microsoft.com/office/3eadf032-0ef8-4d60-9e21-0691d317d103), [use annotation while sharing your screen](https://support.microsoft.com/office/876ba527-7112-437e-b410-5aec7363c473) and use the [whiteboard](https://support.microsoft.com/whiteboard). While the meeting organizer can't turn these features off, you can turn them off for people and groups by using meeting policies in the Teams admin center.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)

[Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md)

[Manage retention policies for Microsoft Teams](retention-policies.md)
