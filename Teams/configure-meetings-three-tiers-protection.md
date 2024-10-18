---
title: Configure Teams meetings with three tiers of protection
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: solution-overview
ms.service: msteams
ms.reviewer: 
ms.date: 12/11/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365solution-overview
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how to configure Teams meetings for better security using three tiers of protection, balancing security with ease of collaboration.
---

# Configure Teams meetings with three tiers of protection

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

The articles in this series provide options for using the compliance features available in Teams and Microsoft 365 to create a meeting environment that meets your compliance requirements. We'll look at the options available with sensitivity labels and templates and how you can use them together with other Teams admin settings.

> [!Note]
> Meeting sensitivity labels and custom meeting templates require Teams Premium.

This article defines four different configurations, starting with a baseline configuration for meetings that don't have specific compliance requirements. Each additional configuration represents a meaningful step up in protection as meeting options become more restricted. The configurations in this article provide examples of how to configure protection for meetings with different levels of sensitivity. Use these examples to understand what's possible and modify the specific settings as needed for your organization.

We'll discuss these three configurations:

- Baseline protection

- Sensitive protection

- Highly sensitive protection

Additionally, we'll discuss a variation of the highly sensitive configuration that is designed for presentations that have minimal interaction from attendees.

## Three tiers at a glance

The following table summarizes the configurations for each tier. Use these configurations as starting point recommendations and adjust the configurations to meet the needs of your organization. Depending on your compliance needs, you may not need every tier.

|&nbsp;|Baseline|Sensitive|Highly sensitive|Highly sensitive presentation|
|:-----|:-----|:-----|:-----|:-----|
|Allow camera for attendees|**On**|**On**|**On**|**Off**|
|Allow mic for attendees|**On**|**On**|**On**|**Off**|
|Apply a watermark to everyone's video feed|**Off**|**Off**|**On**|**On**|
|Apply a watermark to shared content|**Off**|**Off**|**On**|**On**|
|End-to-end encryption|**Off**|**Off**|**On**|**On**|
|Manage what attendees see|**Off**|**On**|**On**|**On**|
|Meeting chat|**On**|**On**|**In-meeting only**|**Off**|
|People dialing in can bypass the lobby|**Off**|**Off**|**Off**|**Off**|
|Prevent copying chat content to clipboard|**Off**|**Off**|**On**|**On**|
|Record meetings automatically|**Off**|**Off**|**Off**|**Off**|
|Who can bypass the lobby?|**People in my org, trusted orgs, and guests**|**People who were invited**|**Only organizers and co-organizers**|**Only organizers and co-organizers**|
|Who can present|**People in my org and guests**|**People in my org and guests**|**Only organizers and co-organizers**|**Only organizers and co-organizers**|
|Who can record|**Organizers, co-organizers, and presenters**|**Organizers and co-organizers**|Disabled due to watermarking|Disabled due to watermarking|

Details on how to configure each tier are covered in:

- [Configure Teams meetings with baseline protection](configure-meetings-baseline-protection.md)
- [Configure Teams meetings with protection for sensitive data](configure-meetings-sensitive-protection.md)
- [Configure Teams meetings with protection for highly sensitive data](configure-meetings-highly-sensitive-protection.md)

## Managing compliance with sensitivity labels and meeting templates

Both meeting templates and sensitivity labels have the ability to enforce certain meeting options. Most options can be enforced as either on or off or can be left unconfigured so the meeting organizer can set them.

> [!IMPORTANT]
> Some features are [controlled by admin policies](meeting-templates-sensitivity-labels-policies.md#policies-labels-templates-and-meetings-settings) and must be enabled there before they can be controlled by meeting templates and sensitivity labels.

Some options are only available in sensitivity labels and some are only available in templates. The following are available in both:

- Chat
- End-to-end encryption
- Lobby options
- Meeting recording
- Prevent copying chat content to clipboard
- Watermarking

Sensitivity labels and templates can be used together to help you meet your compliance needs. For more information, see [Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md).

## Meeting chat

Meeting chat can be an important part of collaboration during a meeting. However, you may want to restrict meeting chat in certain types of meetings to avoid sensitive information being shared there.

As an admin, you can control meeting chat in the following ways:

- **Teams admin meeting policy** (per user or group) can be used to allow chat, allow chat for everyone except anonymous participants, or turn chat off. Can also be used to prevent copying chat content to the clipboard.
- **Sensitivity label meeting option** (per meeting) can enforce chat to be on or off or allowed only during the meeting. Can also be used to prevent copying chat content to the clipboard These options can be left unconfigured to be controlled by a template or the meeting organizer.
- **Meeting template meeting option** (per meeting) can enforce chat to be on or off or allowed only during the meeting. Can also be used to prevent copying chat content to the clipboard. These options can be left unconfigured to be controlled by the meeting organizer.

For the three tiers of protection, we allow chat for baseline and sensitive meetings and restrict it in highly sensitive meetings to in-meeting only. We also prevent copying chat content to the clipboard in sensitive and highly sensitive meetings.

For more information, see [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md).

## Meeting recordings

As an admin, you can control meeting recordings in the following ways:

- The **Meeting recording** admin meeting policy (per user or group)
- The **Recordings automatically expire** (recording deletion) admin meeting policy (per user or group)
- The **Who can record** option in sensitivity labels and meeting templates (per meeting)
- The **Record automatically** option in sensitivity labels and meeting templates (per meeting)

If your organization or certain people or groups within it should never be able to record meetings, you can turn off the feature by using the **Meeting recording** admin meeting policy.

If there are certain types of meetings that must always be recorded, you can enforce the **Record automatically** option using either a meeting template or a sensitivity label.

Within the three tiers discussed here, recording is disabled in highly sensitive meetings because we're using end-to-end encryption and watermarks on shared content and video. If you need to be able to record highly sensitive meetings, make sure you don't enforce watermarks or end-to-end encryption with the sensitivity label. Meeting organizers can still use end-to-end encryption and apply watermarks if a given meeting isn't being recorded.

For more information about managing meeting recording options, see [Manage Microsoft Teams meeting recording options for sensitive meetings](manage-meeting-recording-options.md).

For information about policy-based recording of meetings for compliance, see [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md).

## Meeting with guests and external participants

There are three kinds of external participants who can join meetings:

- Participants from trusted organizations
- Guests
- Anonymous participants

Participants from trusted organizations join meetings via the [external access](manage-external-access.md) feature. You can control what domains, if any, your organization wants to trust. (This setting also affects 1:1 and group chat with people in those domains.)

If [Teams guest access](guest-access.md) is enabled for your organization, then guests will be able to join meetings. Guest access settings can also be used to control guests' screen sharing mode, including disabling screen sharing. (Guest access is also used for inviting guests to teams.)

If the [**Anonymous users can join a meeting** Teams admin setting](anonymous-users-in-meetings.md) is turned on, anonymous participants will be able to join meetings.

While you can turn anonymous join off completely without affecting features other than meetings, both guest access and trusted organizations are used in scenarios other than meetings. If you want to restrict meeting access for these participants but need to leave the features turned on for other reasons, you must use the lobby to prevent these participants from joining a meeting.

## Lobby options

The meeting lobby allows meeting organizers to vet attendees before allowing them into the meeting. Depending on the type of meeting and your compliance requirements, you may want to allow all attendees to bypass the lobby and join the meeting directly, or hold certain types of attendees in the lobby until they're admitted by a meeting organizer. If you wish to prevent certain types of people - such as guests - from attending meetings, you can have them go through the lobby and then the meeting organizer can deny them admittance.

For the baseline tier, we allow everyone except anonymous attendees to bypass the lobby. For sensitive meetings, we allow only people with a meeting invitation to bypass the lobby. For highly sensitive meetings, we require organizers to admit each attendee.

As an admin, you can control the lobby in the following ways:

- The **Who can bypass the lobby?** admin meeting policy (per user or group)
- The **Who can admit from lobby** admin meeting policy (per organizer or group)
- The **People dialing in can bypass the lobby** admin meeting policy (per user or group)
- The **Who can bypass the lobby?** option in sensitivity labels and meeting templates (per meeting)
- The **People dialing in can bypass the lobby** admin meeting policy (per user or group) or in sensitivity labels and meeting templates (per meeting)

These options are also available to the meeting organizer unless they've been locked by a sensitivity label or template.

If you're in a highly regulated industry and you need to manually admit each attendee to all meetings in your organization, you can configure the lobby by using admin meeting policies in the Teams admin center. If your organization has different types of meetings that have different lobby requirements, then we recommend using meeting templates or sensitivity labels to configure these options.

While the admin policy sets a default, you need a template or label to enforce a lobby option.

You can choose to keep the default for **Who can admit from lobby** as **Organizers and presenters** or change it to **Organizers and co-organizers**. This per-organizer policy sets a default that your organizers can change through their **Meeting options**. You must manage this setting through the Teams admin center. Meeting templates and sensitivity labels don't support this policy.

For more information, see [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

## Related topics

[Microsoft cloud for enterprise architects illustrations](/microsoft-365/solutions/cloud-architecture-models)

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)
