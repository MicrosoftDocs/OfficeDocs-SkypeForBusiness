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





|Feature|Meeting organizer|Meeting template|Sensitivity label|Teams admin policy|
|:------|:----------------|:---------------|:----------------|:-----------------|
|Allow chat|Yes|Yes|Yes|When enabled, can be controlled by label, template, or organizer.|
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


Templates can enforce settings

## User-based policies and meeting-based policies



## Different meeting types with the same sensitivity

Using templates and labels together can be useful if you have different types of meetings that have the same sensitivity. For example, if some of your sensitive meetings are interactive and some are presentations where there is minimal interaction from attendees, you can create two templates:
- One that turns off attendee video, audio, and even chat to use for presentations
- One that leaves video, audio, and chat at the discretion of the meeting organizer

Both templates could use the *Sensitive* label which would control additional settings such as who can bypass the lobby and who can present.

## Specify default values that meeting organizers can change

While labels enforce a particular setting, templates can either enforce a setting or allow the meeting organizer to change it. This allows you to implement default settings that meet your compliance needs while giving meeting organizers the option to override the setting if appropriate.

For example, for a baseline level of protection, you might want to use a sensitivity label to enforce who can bypass the lobby. At the same time, you can use a template to set the default for **Who can record** to **Organizers** but allow the meeting organizer to change the setting to **Organizers and presenters** if they need to.

You can assign your baseline protection label to the template so that both are used when a meeting organizer chooses that template.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

