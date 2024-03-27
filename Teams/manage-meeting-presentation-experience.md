---
title: Manage the meeting presentation experience for sensitive Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 12/11/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn about admin options for managing who can present, how content is shared, and how attendees collaborate in sensitive Teams meetings.
---

# Manage the meeting presentation experience for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

Using Teams admin policies, sensitivity labels, and templates, you can control a wide variety of settings that determine the in-meeting experience for participants, including:

- Who can present and who can give or request control
- How content is shared and what collaboration tools are available
- Attendee video, audio, and reactions

Meeting organizers can specify many of theses settings when they create the meeting, but you can enforce specific options for different users and groups in your organization by using admin policies, or for different types or meetings by using sensitivity labels and templates. This can help you meet your compliance needs for different types of meetings and meetings where sensitive information is being shared.

> [!NOTE]
> Meeting settings in sensitivity labels and custom meeting templates require Teams Premium.

## Manage who can present

The following table shows where settings are available to manage who can present in meetings:

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Who can present|Yes|Yes|No|Yes|
|Participants can give or request control|Yes|No|No|No|
|External participants can give or request control|Yes|No|No|No|

By using these controls, you can limit who is able to share content on screen in meetings.

### Default value for who can present in meetings

The Teams admin meeting policy **Who can present** has the following options:

- Only organizers and co-organizers
- People in my org and guests
- Everyone

This setting doesn't enforce the value, but rather specifies the default for new meetings created by users. Users can override this setting and choose any of the other options unless a specific value is enforced by a sensitivity label.

The default value of **Everyone** allows anyone to present in a meeting by default. If you have compliance requirements in your organization around who can present in meetings, consider changing this value to **People in my org and guests** or **Only organizers and co-organizers** to provide a more secure default for users.

To set the **Who can present** policy

1. In the Teams admin center, expand **Meetings**, and then select **Meeting policies**.

1. Select the policy that you want to modify.

1. Under **Meeting join & lobby**, select a value for **Who can present**.

1. Select **Save**.

### Manage who can present by using sensitivity labels

Meeting organizers can choose from the following options for who can present in a meeting:

- People in my org and guests
- Only me and co-organizers
- Specific people
- Everyone

The default value shown when a user creates a meeting is specified by the **Who can present** policy mentioned above.

You can restrict this setting by using a sensitivity label. For sensitive or highly sensitive meetings, consider restricting this setting to **Only me and co-organizers** or **Specific people** by using a sensitivity label.

### Teams admin policy: Participants can give or request control

By default, meeting participants can give control of their shared screen to another participant in the meeting. This is controlled by two Teams admin meeting policies:

- **Participants can give or request control** - This setting determines whether the user with this policy can give control of their shared desktop or window to other meeting participants. It's **On** by default.

- **External participants can give or request control** - This setting determines a guest or anonymous participant can be given control of an internal user's shared screen. It's **Off** by default.

Depending on the compliance requirements of your organization, you can change these settings for some or all of your users.

To configure who can give control of a shared screen

1. In the Teams admin center, expand **Meetings**, and then select **Meeting policies**.

1. Select the policy that you want to modify.

1. Under **Content sharing**:

    1. To prevent participants from giving control of a screen share to others, set **Participants can give or request control** to **Off**.

    1. To prevent external participants from being given control of a screen share, set **External participants can give or request control** to **On**.

1. Select **Save**.

## Manage which content and video is shared with attendees

In meetings where sensitive information is being shared, it can be important to minimize the risk of sharing inappropriate information.

The following table shows settings that can help manage what content and video is shared on screen in meetings.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Screen sharing|Yes|No|No|No|
|Manage what attendees see|No|No|Yes|Yes|

**Screen sharing** is a teams admin policy. With this policy, you can control if meeting attendees can share their entire screen or only a single application. Sharing the entire screen can be convenient, but it can increase the chances of accidentally sharing inappropriate information such as an email or open document. Consider if you want to restrict sharing to a single application for users or departments that often present sensitive information. You can also turn off screen sharing entirely with this policy. For more information, see [Manage meeting policies for content sharing](meeting-policies-content-sharing.md).

**Manage what attendees see** is an option available to meeting organizers that can also be set by using a template. When this option is enabled, meeting organizers can control what content is shared on screen and who's video is visible. Organizers must intentionally bring shared content and video on screen before attendees can see it. This can help minimize the risk of sharing inappropriate content in a meeting. Consider if you want to enable or enforce this experience for sensitive meetings by using a meeting template. For more information, see [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16).

## Manage presentation tools

Teams offers several presentation tools that allow for interactive participation of meeting attendees. The following table shows features that can help manage these tools.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|PowerPoint Live|Yes|No|No|No|
|Whiteboard|Yes|No|No|No|
|Shared notes|Yes|No|No|No|

Each of these features can be managed through admin policies, but not through templates or sensitivity labels, nor by the meeting organizer. As such, they can be applied to users or groups, but not to specific meetings. For more information, see [Meeting policy settings - Content sharing](meeting-policies-content-sharing.md).

If you have meetings where sensitive information is being shared, you may want to disable Whiteboard and shared notes to avoid having sensitive information added to them.

PowerPoint Live allows attendees to navigate forward and back in a PowerPoint presentation being shared on screen. This may allow attendees to see sensitive information before it's presented by the organizer.

Consider if there are users or groups in your organization who shouldn't use these features to avoid sharing sensitive information.

## Manage how meeting attendees interact

The following table shows features that can help manage how meeting attendees interact during a meeting.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Allow camera for attendees|No|No|Yes|Yes|
|Allow mic for attendees|No|No|Yes|Yes|
|Reactions|Yes|No|Yes|Yes|

Attendee audio and video can make it easy for attendees to communicate during a meeting. These can both be controlled by the meeting organizer or by a meeting template. Depending on the type of meeting, you may want to allow or restrict these capabilities.

For meetings that are presentations with minimal interaction from attendees, turning video and audio off can minimize distractions.

When recording meetings, video from participants might be considered personal data and infer regulatory requirements.

If you choose to turn off reactions, remember that this will disable the hand-raise feature. (For presentation-style meetings, the Q&A feature may allow the needed interaction for attendees to ask questions.)

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Manage access to Microsoft Whiteboard for your organization](/microsoft-365/whiteboard/manage-whiteboard-access-organizations)
