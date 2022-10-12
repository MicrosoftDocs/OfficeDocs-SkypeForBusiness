---
title: Configure Teams meetings with three tiers of protection
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
  - m365solution-overview
appliesto: 
  - Microsoft Teams
description: 
---

# Configure Teams meetings with three tiers of protection

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

The articles in this series provide recommendations for using the compliance features available in Teams and Microsoft 365 to create a meeting environment that meets your compliance requirements. We'll look at the options available with sensitivity labels and how you can use them together with other Teams admin settings.

This article defines four different configurations, starting with a baseline configuration for meetings that don't have specific compliance requirements. Each additional configuration represents a meaningful step up in protection as meeting options become more restricted. The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices.

We'll discuss these three configurations:

- Baseline protection

- sensitive protection

- Highly sensitive protection

Additionally, we'll discuss a variation of the highly sensitive configuration for presentations that have minimal interaction from attendees.

## Three tiers at a glance

The following table summarizes the configurations for each tier. Use these configurations as starting point recommendations and adjust the configurations to meet the needs of your organization. You may not need every tier.

|&nbsp;|Baseline|Sensitive|Highly sensitive|Highly sensitive presentation|
|:-----|:-----|:-----|:-----|:-----|
|Allow guest one-time passcode|Yes|Yes|No|No|
|Allow meeting chat|**Enabled**|**Enabled**|**In-meeting only**|**No**|
|Always let callers bypass the lobby|Yes|No|No|No|
|End-to-end encryption|No|No|Yes|Yes|
|Prevent copy & paste of meeting chat|No|No|Yes|Yes|
|Prevent screen capture|No|No|Yes|Yes|
|Record automatically|No|No|No|No|
|Watermark meeting content|No|No|No|Yes|
|Who can bypass the lobby|**People in my organization, people in trusted domains, and guests**|**People I invite**|**Only me and co-organizers**|**Only me and co-organizers**|
|Who can present|**People in my organization and guests**|**People in my organization and guests**|**Only me and co-organizers**|**Specific people**|
|Who can record|**Organizers and presenters**|**Organizer and co-organizers**|**Organizer and co-organizers**|Disabled due to watermarking|
|Who can transcribe|**Organizers and presenters**|**Organizer and co-organizers**|**Organizer and co-organizers**|**Organizer and co-organizers**|

## Managing compliance with sensitivity labels and meeting templates


## Meeting chat

## Meeting recordings

## Meeting with guests and external participants

## Lobby options

## Anonymous participants

## The attendee experience

## Related topics

[Microsoft cloud for enterprise architects illustrations](/microsoft-365/solutions/cloud-architecture-models)
