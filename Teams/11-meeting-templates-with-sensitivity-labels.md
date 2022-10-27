---
title: Use Teams meeting templates with sensitivity labels
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
description: 
---

# Use Teams meeting templates with sensitivity labels

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]



Pivots

presentation meetings vs. interactive

templates for setting defaults even if they can be changed

The following table shows a list of Teams features that may be useful for managing sensitive meetings in your organization and where they can be configured.

|Feature|Meeting organizer|Meeting template|Sensitivity label|Teams admin policy|
|:------|:----------------|:---------------|:----------------|:-----------------|
|Allow chat|Yes|Yes|Yes|Yes|
|Allow dial-in users to bypass the lobby|Yes|Yes|Yes|Yes|
|Disable camera for attendees|Yes|Yes|No|No|
|Disable mic for attendees|Yes|Yes|No|No|
|End-to-end encryption|Yes|No|Yes|Yes|
|Manage what attendees see|Yes|Yes|No|No|
|Prevent copying chat content to clipboard|No|No|Yes|No|
|Record automatically|Yes|Yes|Yes|No|
|Watermark camera streams|Yes|No|Yes|Yes|
|Watermark screenshare|Yes|No|Yes|Yes|
|Who can bypass the lobby|Yes|Yes|Yes|Yes|
|Who can present|Yes|No|Yes|No|
|Who can record|Yes|Yes|Yes|No|

Can disable chat or restrict anonymous participants.

|Feature|Teams admin policy|Sensitivity label|Meeting template|Meeting organizer|
|:------|:-----------------|:----------------|:---------------|:----------------|
|Allow chat|Can be set to On, Off, or On for everyone except anonymous participants. If set to Off, then not available in labels, templates, or meeting settings.|Can disable chat or restrict it to meeting-only.|Can disable or enable chat or restrict it to meeting-only.|Can disable or enable chat or restrict it to meeting-only.|
|Allow dial-in users to bypass the lobby|Can prevent dial-in attendees from bypassing the lobby|Can prevent dial-in attendees from bypassing the lobby|Can prevent dial-in attendees from bypassing the lobby|Can prevent dial-in attendees from bypassing the lobby|
|Disable camera for attendees|No setting|No setting|Can prevent or allow camera for attendees|Can prevent or allow camera for attendees if not locked by a template|
|Disable mic for attendees|No setting|No setting|Can prevent or allow mic for attendees|Can prevent or allow mic for attendees if not locked by a template|
|End-to-end encryption|When On, end-to-end encryption can be turned on by a sensitivity label or the meeting organizer.|No setting|No setting|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a sensitivity label.|
|Manage what attendees see|No setting|No setting|Can be set to On or Off and can enforce the setting or allow the meeting organizer to change it.|Can be set to On or Off unless enforced by a template.|
|Prevent copying chat content to clipboard|No setting|Can prevent the meeting chat from being copied. (Does not apply to anonymous participants.)|No setting|No setting|
|Record automatically|No setting|Can enforce or prevent automatic meeting recording.|Can be set to On or Off and can enforce the setting or allow the meeting organizer to change it. Sensitivity label overrides if used.|Can be set to On or Off unless enforced by a template or sensitivity label.|
|Watermark camera streams|Can be set to On or Off. If set to off, then not available in sensitivity labels or meeting settings.|Can enforce or prevent watermarks on camera streams.|No setting|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a sensitivity label.|
|Watermark screenshare|Can be set to On or Off. If set to off, then not available in sensitivity labels or meeting settings.|Can enforce or prevent watermarks on screenshared content.|No setting|Meeting organizer can turn on or off unless the setting is disabled by admin policy or enforced on or off by a sensitivity label.|
|Who can bypass the lobby|||||
|Who can present|No setting||No setting||
|Who can record|No setting||||


Templates can enforce settings


The following label settings are always controlled by the sensitivity label if used:


The following label settings can left unconfigured and controlled by a template or the meeting organizer:
- Lobby restrictions
- 

## Sensitivity label settings take precedence

Whenever a sensitivity label is used, the settings configured in the label take precedence over any template or meeting organizer setting.

While lobby restrictions can be disabled in the label - allowing either a template or the meeting organizer to control them - the remaining label settings always enforce a condition and override any template or meeting organizer settings. These settings are:

- Who can present
- Who can record
- Automatic recording
- End-to-end encryption
- Watermarks
- Chat settings

While chat and recording settings are available in templates, the label settings will always take precedence if a label is used.

## User-based policies and meeting-based policies



## Different meeting types with the same sensitivity

Using templates and labels together can be useful if you have different types of meetings that have the same sensitivity. For example, if some of your sensitive meetings are interactive and some are presentations where there is minimal interaction from attendees, you can create two templates:
- One that turns off attendee video and audio to use for presentations
- One that leaves video and audio at the discretion of the meeting organizer

Both templates could use the *Sensitive* label which would control additional settings such as who can bypass the lobby and who can present.

## Specify default values that meeting organizers can change

While labels enforce a particular setting, templates can either enforce a setting or allow the meeting organizer to change it. This allows you to implement default settings that meet your compliance needs while giving meeting organizers the option to override the setting if appropriate.

For example, for a baseline level of protection, you might want to use a sensitivity label to enforce who can bypass the lobby. At the same time, you can use a template to set the default for **Who can record** to **Organizers** but allow the meeting organizer to change the setting to **Organizers and presenters** if they need to.

You can assign your baseline protection label to the template so that both are used when a meeting organizer chooses that template.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

