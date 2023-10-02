---
title: Overview of custom meeting templates in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ralphmaamari
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
description: Learn about custom meeting templates in Microsoft Teams Premium.
---

# Overview of custom meeting templates in Microsoft Teams

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

[Microsoft Teams Premium](enhanced-teams-experience.md) includes the ability to create custom meeting templates. Meeting templates can be used to control meeting options that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

Meeting templates can be used to enforce meeting options or to set defaults. Each template option can be locked so the meeting organizer can't change it, or can be left unlocked for the meeting organizer to change if needed.

The following meeting options can be controlled by using a meeting template:

|Option|Description|
|:------|:----------|
|Meeting chat|Specifies if the meeting chat is available. Can also be used to prevent chat before and after the meeting.|
|End-to-end encryption|Specifies if the meeting is encrypted.|
|Lobby|Specifies who can bypass the lobby and join the meeting directly.|
|Manage what attendees see|Specifies if meeting organizers can preview and approve content being shared on screen before other meeting participants can see it.|
|Allow mic and camera for attendees|Specifies if attendees can unmute and use their camera.|
|Announce when people dialing in join or leave|Specifies if a sound plays when people calling in by phone join or leave the meeting.|
|Q&A|Specifies if attendees can use the Q&A feature to ask questions during the meeting.|
|Allow reactions|Specifies if attendees can use reactions or raise their hand in the meeting.|
|Recording|Specifies who can record and if the meeting is recorded automatically.|
|Sensitivity label|Specifies the sensitivity label to be used for the meeting.|
|Enable watermark for screenshare and for video|Specifies if watermarks are used for camera feeds and content that is shared on screen in the meeting.|

Some examples of when a template can be useful are:

- Enforcing automatic meeting recording for certain types of meetings.
- Restricting chat and attendee camera and audio and using the Q&A feature for presentation-style meetings.
- Using a stricter default for who can bypass the lobby, but allowing the meeting organizer to change the option if needed.

To learn how to create meeting templates, see [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md).

> [!NOTE]
> The option to select a custom meeting template when creating a new meeting isn't available on Outlook for Mac or Outlook on the web.

## Templates with sensitivity labels

Templates have the option of specifying a sensitivity label. Labels can also be applied directly to meetings, independent of templates. Sensitivity labels can control some of the same meeting options as templates:

- End-to-end encryption
- Meeting chat
- Record meetings automatically
- Who can bypass the lobby?
- Who can present
- Who can record
- Enable watermark for screenshare
- Enable watermark for video

If any of these options are configured in the label, they will override these options in the template.

## Templates included with Teams

Teams Premium includes the following default meeting template:

- [Virtual appointment](virtual-appointment-meeting-template.md)

Additionally, these templates are available in Teams for Education:

- Class
- Lecture
- [Webinar](set-up-webinars.md)

For information about the class and lecture templates, see [Use education templates for Teams meetings](https://support.microsoft.com/topic/9567d25f-3ac5-4fcf-9b66-18f70e5d42b3).

You can update the options on these templates if you need to.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md)

[Meetings, webinars, and live events](quick-start-meetings-live-events.md)
