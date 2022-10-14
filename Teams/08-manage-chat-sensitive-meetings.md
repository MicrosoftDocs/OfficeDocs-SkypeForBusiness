---
title: Manage chat for sensitive Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: high
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
appliesto: 
  - Microsoft Teams
description: 
---

# Manage chat for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

By default, all meeting attendees can chat both during and after the meeting. Meeting organizers can turn this feature off or allow chat only during the meeting.

If you have compliance requirements for certain types of meetings, you can manage how and when chat is enabled by using a combination of Teams admin policies, meeting templates, and sensitivity labels.

The following table show what chat-related controls are available and where they can be managed.

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Attendees can chat|Yes|Yes|Yes|Yes|
|Prevent copy & paste of meeting chat|No|No|Yes|No|
|Enable Q&A|Yes|No|No|Yes|
|Shared notes|No|No|No|Yes|


Chat off to avoid PII

Anonymous only at policy level

in-meeting only if other chat otherwise used



Chat in meetings on/off/NoAnonymous (Policy)

Meeting chat on/off/meeting-only (Template)
Allow meeting chat on/off/meeting-only (Meeting organizer)
Allow meeting chat on/off/meeting-only (Sensitivity label)

Prevent copy & paste of meeting chat (Sensitivity label)

Shared notes (Policy)
Enable Q&A (Meeting organizer)
Teams Q&A (Policy)

Chat retention (Purview)

