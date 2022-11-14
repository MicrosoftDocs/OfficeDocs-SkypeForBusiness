---
title: Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings
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
description: Learn how to use Teams admin policies together with sensitivity labels and meeting templates to enhance security and compliance for sensitive meetings.
---

# Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

In Teams meetings, meeting organizers can configure [a variety of settings](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e) that determine which features are available in the meeting. As an administrator, you can disable or enforce specific values for these settings by using a combination of admin policies, sensitivity labels, and meeting templates.

[Meeting templates](custom-meeting-templates-overview.md) are created and managed in the Teams admin center. Sensitivity labels are created and manged in the Microsoft Purview compliance portal. 

> [!Note]
> Meeting settings in sensitivity labels and custom meeting templates require Teams Premium.

By using admin policies, templates, and labels together you can make possible a variety of meeting scenarios to help meet the compliance and business needs for the different departments in your organization.

The following table shows a list of Teams features that may be useful for managing meetings with different compliance needs in your organization and where they can be configured.

|Feature|Teams admin policy|Sensitivity label|Meeting template|Meeting organizer|
|:----|:----|:----|:----|:----|
|Allow camera for attendees|The IP video and Mode for IP video admin policy settings determine which participants can use their cameras.|No setting|Can prevent or allow camera for attendees. Setting can be enforced or meeting organizer can be allowed to change.|Can prevent or allow camera for attendees if not locked by a template.|
|Allow mic for attendees|The Mode for IP audio setting determines which participants can use their mics.|No setting|Can prevent or allow mic for attendees. Setting can be enforced or meeting organizer can be allowed to change.|Can prevent or allow mic for attendees if not locked by a template.|
|Apply a watermark to everyone's video feed|Can be set to On or Off. If set to Off, then not available in sensitivity labels, meeting templates, or meeting settings.|Can enforce or prevent watermarks on participants' video feeds, or leave the setting uncontrolled.|Can enforce or prevent watermarks on participants' video feeds unless the setting is controlled by a sensitivity label.|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a meeting template or sensitivity label.|
|Apply a watermark to shared content|Can be set to On or Off. If set to Off, then not available in sensitivity labels, meeting templates, or meeting settings.|Can enforce or prevent watermarks on content shared on screen or leave the setting uncontrolled.|Can enforce or prevent watermarks on content shared on screen unless the setting is controlled by a sensitivity label.|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a meeting template or sensitivity label.|
|End-to-end encryption|When On, end-to-end encryption can be turned on by a sensitivity label, meeting template, or the meeting organizer.|Can enforce or prevent end-to-end encryption or leave the setting uncontrolled.|Can enforce or prevent end-to-end encryption unless the setting is controlled by a sensitivity label.|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a meeting template or sensitivity label.|
|Manage what attendees see|No setting|No setting|Can be set to On or Off and can enforce the setting or allow the meeting organizer to change it.|Meeting organizer can turn on or off unless the setting is enforced on or off by a meeting template.|
|Meeting chat|Can be set to On, Off, or On for everyone except anonymous participants. If set to Off, then the chat setting is disabled in labels, templates, and meeting settings.|Can enforce chat to be On, Off, or meeting-only, or leave the setting uncontrolled.|If enabled in admin policy and not controlled by a sensitivity label, can be set to On, Off, or meeting-only. Setting can be enforced or meeting organizer can be allowed to change.|If enabled by admin policy and not enforced by a sensitivity label or template, meeting owner can set to On, Off, or meeting-only.|
|People dialing in can bypass the lobby|Sets the default setting for new meetings.|If the label is controlling who can bypass the lobby, this setting is enforced On or Off, otherwise it is uncontrolled.|If not controlled by a sensitivity label, can be set to On or Off. Setting can be enforced or meeting organizer can be allowed to change.|If not enforced by a sensitivity label or template, meeting owner can set to On or Off.|
|Prevent copying chat content to clipboard|No setting|Can prevent the meeting chat from being copied. (Does not apply to anonymous participants.)|No setting|No setting|
|Record automatically|No setting|Can enforce or prevent automatic meeting recording or be left uncontrolled.|If not controlled by a sensitivity label, can be set to On or Off and can enforce the setting or allow the meeting organizer to change it.|Meeting organizer can turn on or off unless the setting is enforced on or off by a meeting template or sensitivity label.|
|Who can bypass the lobby|Sets the default setting for new meetings.|Can enforce a particular option for who can bypass the lobby, or can be left uncontrolled.|If not controlled by a sensitivity label, selects a setting for who can bypass the lobby. Setting can be enforced or meeting organizer can be allowed to change.|Meeting organizer can choose who can bypass the lobby unless the setting is enforced by a label or template.|
|Who can present|No setting|Can enforce settings of everyone, authenticated attendees, organizers, or specific people, or can be left uncontrolled.|No setting|Meeting organizer can select who can present unless enforced by a sensitivity label.|
|Who can record|No setting|Can enforce settings of organizers or organizers and presenters, or can be left uncontrolled.|If not controlled by a sensitivity label, selects a setting of organizers or organizers and presenters.  Setting can be enforced or meeting organizer can be allowed to change.|Meeting organizer can choose who can record - organizers or organizers and presenters - unless the setting is enforced by a label or template.|

## Sensitivity label settings take precedence

Whenever a sensitivity label is used, the settings configured in the label take precedence over any template or meeting organizer settings.

While lobby restrictions can be disabled in the label - allowing either a template or the meeting organizer to control them - the remaining label settings always enforce a condition and override any template or meeting organizer settings. These settings are:

- Who can present
- Who can record
- Automatic recording
- End-to-end encryption
- Watermarks
- Chat settings

While chat and recording settings are available in templates, the label settings will always take precedence if a label is used.

## User-based policies and meeting-based policies

Teams policies - including meeting policies - apply at the user or group level. Sensitivity label and template settings apply at the individual meeting level where those labels and templates are used. Consider where it makes sense to configure settings in Teams admin policies versus sensitivity labels or templates.

Here are a few examples:

If you want different default lobby settings for the research department and the marketing department, you can configure these defaults using admin policies and further modify them with labels or templates.

If you want watermarks available only for governance officials, you can enable them only for those people using an admin policy. You can then have labels or templates that enforce watermarking, but the watermarking will only be used in meetings organized by governance officials.

## Different meeting types with the same sensitivity

Using templates and labels together can be useful if you have different types of meetings that have the same sensitivity. For example, if some of your sensitive meetings are interactive and some are presentations where there is minimal interaction from attendees, you can create two templates:
- One that turns off attendee video and audio to use for presentations
- One that leaves video and audio at the discretion of the meeting organizer to use for interactive meetings

Both templates could use the *Sensitive* label which would control additional settings such as who can bypass the lobby and who can present.

## Specify default values that meeting organizers can change

While labels generally enforce a particular setting, templates can either enforce a setting or allow the meeting organizer to change it. This allows you to implement default settings that meet your compliance needs while giving meeting organizers the option to override the setting if appropriate.

For example, for a baseline level of protection, you might want to use a sensitivity label to turn off watermarking. At the same time, you can use a template to set the default for who can bypass the lobby, but allow the meeting organizer to change the setting if they need to.

You can assign your baseline protection label to the template so that both are used when a meeting organizer chooses that template.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)