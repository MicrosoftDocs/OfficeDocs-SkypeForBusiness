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

To set the **Who can present in meetings** policy

1. In the Teams admin center, expand **Meetings**, and then select **Meeting policies**.

1. Select the policy that you want to modify.

1. Under **Participants & Guests**, select a value for **Who can present in meetings**.

1. Select **Save**.

### Sensitivity labels and templates: Who can present in meetings

Meeting organizers can choose from the following options for who can present in a meeting:

- People in my organization and guests
- Only me and co-organizers
- Specific people
- Everyone

The default value shown when a user creates a meeting is specified by the **Who can present in meetings** policy mentioned above.

You can restrict this setting by using using a sensitivity label. For sensitive or highly sensitive meetings, consider restricting this setting to **Only me and co-organizers** or **Specific people** by using a sensitivity label.

### Teams admin policy: Participants can give or request control

By default, meeting participants can give control of their shared screen to another participant in the meeting. This is controlled by two Teams admin meeting policies:

- **Participants can give or request control** - This setting determines if meeting participants can give control of their shared screen to another participant or request control from another participant. It is **On** by default.

- **External participants can give or request control** - This setting determines an external participant can be given control of a shared screen. It is **Off** by default.

Depending on the compliance requirements of your organization, you can change these settings for some or all of your users.

To configure who can give control of a shared screen

1. In the Teams admin center, expand **Meetings**, and then select **Meeting policies**.

1. Select the policy that you want to modify.

1. Under **Content sharing**:

    1. To prevent participants from giving control of a screen share to others, set **Participants can give or request control** to **Off**.

    1. To prevent external participants from being given control of a screen share, set **External participants can give or request control** to **Off**.

1. Select **Save**.


## Manage what attendees can see


|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Manage what attendees see|Yes|Yes|No|No|
|Screen sharing mode|No|No|No|Yes|

Manage what attendees see (Meeting organizer) on/off
Manage what attendees see (Template) on/off

Screen sharing mode (Policy) entire screen/single application/not enabled


## Manage presentation tools

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|PowerPoint Live|No|No|No|Yes|
|Whiteboard|No|No|No|Yes|
|Shared notes|No|No|No|Yes|


PowerPoint Live (Policy) on/off
Whiteboard (Policy) on/off
Shared notes (Policy) on/off


## Manage how meeting attendees interact


|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Allow attendee video|Yes|Yes|No|No|
|Attendees can unmute|Yes|Yes|No|No|
|Meeting reactions|Yes|Yes|No|Yes|


Allow attendee video (Template) on/off
Allow camera for attendees (Meeting organizer) on/off

Allow mic for attendees (Meeting organizer) on/off
Attendees can unmute (Microphone) (Template) on/off


Allow reactions (Meeting organizer)
Meeting reactions (Policy)
Reactions (Template)



