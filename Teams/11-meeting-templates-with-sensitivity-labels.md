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

An advantage of using templates is that you can create multiple templates that use the same sensitivity label which lock different settings. For example, if some of your sensitive meetings are presentations where there is minimal interaction from attendees, you can create a template that turns off attendee video and even chat, and another template that leaves those options to the meeting organizer. Both templates would use the *Sensitive* label.

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

## User-based policies and meeting-based policies


## Different meeting types with the same sensitivity



## Specify default values that meeting organizers can change


