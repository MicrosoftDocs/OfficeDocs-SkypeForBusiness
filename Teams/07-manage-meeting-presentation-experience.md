---
title: Manage meeting presentation experience
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

# Manage meeting presentation experience

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

[!INCLUDE[Teams Premium COE](includes/teams-premium-coe.md)]

Choose co-organizers (Meeting organizer)
Enable green room (Meeting organizer) on/off



## Manage who can present

The following table shows where settings are available to manage who can present in meetings:

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Who can present|Yes|No|Yes|Yes|
|Participants can give or request control|No|No|No|Yes|
|External participants can give or request control|No|No|No|Yes|


Template, label, and organizer:
People in my organization and guests
Only me and co-organizers
Specific people
Everyone

### Teams admin policy: Who can present in meetings

The Teams admin meeting policys **Who can present in meetings** has the following options:

- Organizers, but user can override
- Everyone in the organizaition, but user can override
- Everyone, but user can override

This setting specifies the default for new meetings created by users. Users can override this setting and choose any of the other options unless a specific value is locked in by a template or sensitivity label.

The default value of **Everyone, but user can override** allows anyone to present in a meeting by default. If you have compliance requirements in your organization around who can present in meetings, consider changing this value to **Everyone in the organization** or **Organizers** to provide a more secure default for users.

### Sensitivity labels and templates: Who can present in meetings

Meeting organizers can choose from the following options for who can present in a meeting:

- People in my organization and guests
- Only me and co-organizers
- Specific people
- Everyone

The default value is specified by the **Who can present in meetings** policy mentioned above.

You can restrict this setting by using either a template or a sensitivity label. If values are specified in both, the sensitivity label setting is used.





### Teams admin policy: Participants can give or request control

Participants can give or request control (Policy) on/off

External participants can give or request control (Policy) on/off


## Manage what attendees can see

Manage what attendees see (Meeting organizer) on/off
Manage what attendees see (Template) on/off

Screen sharing mode (Policy) entire screen/single application/not enabled


## Manage presentation tools

PowerPoint Live (Policy) on/off
Whiteboard (Policy) on/off
Shared notes (Policy) on/off


## Manage how meeting attendees interact

Allow attendee video (Template) on/off
Allow camera for attendees (Meeting organizer) on/off

Allow mic for attendees (Meeting organizer) on/off
Attendees can unmute (Microphone) (Template) on/off


Allow reactions (Meeting organizer)
Meeting reactions (Policy)
Reactions (Template)



