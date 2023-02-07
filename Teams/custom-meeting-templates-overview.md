---
title: Overview of custom meeting templates in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ralphmaamari
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

Microsoft Teams Premium includes the ability to create custom meeting templates. Meeting templates can be used to control meeting settings that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

Meeting templates can be used to enforce settings or to set defaults. Each template setting can be locked so the meeting organizer can't change it, or can be left unlocked for the meeting organizer to change if needed.

The following meeting settings can be controlled by using a meeting template:

|Setting|Description|
|:------|:----------|
|Chat|Specifies if the meeting chat is available. Can also be used to prevent chat before and after the meeting.|
|End-to-end encryption|Specifies if the meeting is encrypted.|
|Lobby|Specifies who can bypass the lobby and join the meeting directly.|
|Manage what attendees see|Specifies if meeting organizers can preview and approve content being shared on screen before other meeting participants can see it.|
|Mic and camera for attendees|Specifies if attendees can unmute and use their camera.|
|Notify when callers join and leave|Specifies if a sound plays when people calling in by phone join or leave the meeting.|
|Q&A|Specifies if attendees can use the Q&A feature to ask questions during the meeting.|
|Reactions|Specifies if attendees can use reactions or raise their hand in the meeting.|
|Recording|Specifies who can record and if the meeting is recorded automatically.|
|Sensitivity label|Specifies the sensitivity label to be used for the meeting.|
|Watermarks|Specifies if watermarks are used for camera feeds and content that is shared on screen in the meeting.|

Some examples of when a template can be useful are:

- Enforcing automatic meeting recording for certain types of meetings.
- Restricting chat and attendee camera and audio and using the Q&A feature for presentation-style meetings.
- Using a stricter default for who can bypass the lobby, but allowing the meeting organizer to change the setting if needed.

To learn how to create meeting templates, see [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md).

## Templates with sensitivity labels

Templates have the option of specifying a sensitivity label. Labels can also be applied directly to meetings, independent of templates. Sensitivity labels can control some of the same settings as templates:

- End-to-end encryption
- Meeting chat
- Record automatically
- Who can bypass the lobby
- Who can present
- Who can record
- Watermarks

If any of these settings are configured in the label, they will override these settings in the template.

## Templates included with Teams

Teams Premium includes several default meeting templates that you can make available to your users:

- Large Meeting
- Protected meeting
- Town hall
- [Virtual appointment](virtual-appointment-meeting-template.md)
- [Webinar](set-up-webinars.md)

Additionally, these templates are available in Teams for Education:

- Class
- Lecture
- [Webinar](set-up-webinars.md)

You can update the settings on these templates if you need to.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md)

[Meetings, webinars, and live events](quick-start-meetings-live-events.md)
