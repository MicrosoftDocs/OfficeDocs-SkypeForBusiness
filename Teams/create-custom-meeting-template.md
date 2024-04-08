---
title: IT admins - Create a custom meeting template in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: janineco
ms.date: 01/08/2024
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how Microsoft Teams administrators can create a custom meeting template to set or enforce meeting organizer options for enhanced meeting security and compliance.
---

# IT admins - Create a custom meeting template in Microsoft Teams

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

Microsoft Teams custom meeting templates (a Teams Premium feature) allow you to specify values for many of the meeting options available to meeting organizers. Templates can be used to configure options that meeting organizers can change or can be used to lock options so that meeting organizers can't change them. For more information about custom meeting templates, see [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md).

You can create up to 50 custom templates. See [Manage meeting templates in Microsoft Teams](manage-meeting-templates.md) for information on how to manage which templates are available to your users.

For each option in the template, you can define the following:

- **Default value** - This is the value that is applied to a meeting when the template is used.
- **Visibility** - This determines if the meeting organizer can see this option.
- **Lock status** - This determines if the meeting organizer can change the option that was set by the template. If the option is locked, the meeting organizer can't change it.

## Video demonstration

Watch this video for a walkthrough of the procedures described in this article.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW11u1o]

## Create a custom meeting template

Use this procedure to create a custom meeting template in the Teams admin center.

To create a custom meeting template

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**.
1. Type a name and description for the template. Note that the name and description will truncate after 40 characters when viewed in Teams, but the full name and description are viewable on hover.
1. Choose the options that you want to use for this template. (See the sections below for descriptions of each option.)
1. To prevent the meeting organizer from changing an option, select the option and then select **lock**.
1. To prevent the meeting organizer from seeing an option, select the option and then select **Hide**.
1. Select **Save**.

Once the template has been created, it may take up to 24 hours to be available to your users.

Note that if you change the options of an existing template, the changes affect new meetings scheduled using that template as well as any meetings that have already been scheduled with that template.

#### Security

|Option|Description|
|:------|:----------|
|Apply sensitivity label|Specifies the meeting sensitivity label to be used for the meeting. Note that the sensitivity label may override certain options in the template. Once you save the template, the label can't be changed in the template, but organizers can change the label if you leave the option unlocked.|
|Who can bypass the lobby?|Specifies who can bypass the lobby and join the meeting directly.|
|People dialing in can bypass the lobby|Specifies if people calling in by phone can bypass the lobby and join the meeting directly.|
|End-to-end encryption|Specifies if the meeting uses end-to-end encryption. Recording and transcription don't work if this is on.|
|Enable watermark for screenshare|Specifies if a watermark is overlaid on content that is shared on screen in the meeting.|
|Enable watermark for video|Specifies if a watermark is overlaid on attendees' video feeds in the meeting.|
|Restrict participants from copying or forwarding meeting chat messages|Prevents participants from copying or forwarding content in the meeting chat.|

#### Audio & video

|Option|Description|
|:------|:----------|
|Allow mic for attendees|When **On**, attendees can unmute.|
|Allow camera for attendees|When **On**, attendees can turn on their cameras.|

#### Recording & transcription

|Option|Description|
|:------|:----------|
|Record meetings automatically|When **On** meetings are recorded automatically.|
|Who can record|Specifies whether meetings can be recorded by organizers and co-organizers only or by organizers, co-organizers, and presenters.|
|Copilot|Specifies if Copilot uses a meeting transcript.|

#### Roles

|Option|Description|
|:------|:----------|
|Announce when people dialing in join or leave|Specifies if a sound is played when people calling in by phone join or leave the meeting.|

#### Meeting engagement

|Option|Description|
|:------|:----------|
|Meeting chat|Specifies if the meeting chat is available. Can also be used to prevent chat before and after the meeting.|
|Allow reactions|Specifies if attendees can use reactions in the meeting. This must be **On** for the raise hand feature to work.|
|Q&A|Specifies if attendees can use the Q&A feature to ask questions during the meeting.|
|Manage what attendees see|When **On**, meeting organizers can preview and approve content being shared on screen before other meeting participants can see it.|

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
