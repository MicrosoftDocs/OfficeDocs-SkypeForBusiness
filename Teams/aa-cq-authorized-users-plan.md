---
title: Plan for Auto attendant and Call queue authorized users
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 03/04/2024
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
f1.keywords:
- CSH
ms.custom:
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn the requirements needed to set up authorized users for Auto attendants and Call queues.
---

# Plan for Auto attendant and Call queue authorized users

This article is for IT Pros and administrators who want to delegate certain Auto attendant or Call queue configuration capabilities to the users in their organization. This article describes benefits and licensing requirements. After reading this article, see [Set up authorized users](aa-cq-authorized-users.md) and [Manage voice applications policies](manage-voice-applications-policies.md) for more information.

## Benefits

Through **authorized users**, you enable users in your organization—for example, business owners, team leads, supervisors of call queues--to manage day-to-day operational changes directly. This includes changes such as updating business hours, holiday greetings, and after hours call routing.

## Requirements

For basic configuration features, authorized users must have a user phone number and Teams Phone license assigned to them and authorized users must be “voice enabled". For advanced configuration features located in the Customer Calls app, you must assign a Teams Phone and Teams Premium license to authorized users. For a list of features that require a Teams Premium license, see [Licensing requirements for configuration features](#licensing-requirements-for-configuration-features).

Keep in mind the following:

- An authorized user has the same capabilities across the Auto attendant and Call queues they're authorized for.
- You can only assign one voice applications policy per user.
- You can't delegate an authorized user to perform the following actions:
  - Create or delete Auto attendants or Call queues
  - Manage Resource Accounts
  - Change the calling ID used in Call queue
  - Change the call queue overflow limit or agent timeout values

## Steps for setting up authorized users

To create an authorized user, you must complete the following steps:  

- Step 1 - Assign licenses and enable users for voice  
- Step 2 - Assign phone numbers to your users
- Step 3 - Create a Teams voice applications policy
- Step 4 - Assign the voice applications policy to the user
- Step 5 - Create an Auto attendant or Call queue and assign licensed resource accounts
- Step 6 - Assign authorized users to the relevant Auto attendant or Call queue

For information on configuring these steps, see [Set up authorized users](aa-cq-authorized-users.md).

## Configuration features

Basic configuration features for Auto attendants and Call queues are available to all authorized users with a Teams Phone license. However, advanced configuration features require a Teams Premium license.

### Auto attendants

You can delegate an authorized user to perform some or all of the following configuration tasks for Auto attendants:

| Configuration feature | Teams Premium license required |
|-----------------------|--------------------------------|
|Business hours greeting|✖️|
|After hours greeting|✖️|
|Holiday greeting|✖️|
|Business hours|✔️|
|Holiday dates and hours|✔️|
|Business hours call routing|✔️|
|After hours call routing|✔️|
|Holiday hours call routing|✔️|
|Real-time auto attendant metrics|✔️|
|Historical auto attendant metrics|✖️ Using Power BI<br>✔️ Using Customer Calls app|

For more information about these configuration features, see [Manage voice applications policies](manage-voice-applications-policies.md).

### Call queues

You can delegate an authorized user to perform some or all of the following configuration tasks for Call queues:

| Configuration feature | Teams Premium license required |
|-----------------------|--------------------------------|
|Welcome greeting|✖️|
|Music on Hold|✖️|
|Shared voicemail greeting for call overflow|✖️|
|Shared voicemail greeting for call timeout|✖️|
|Shared voicemail greeting for no agents|✖️|
|Membership|✔️|
|Conference mode|✔️|
|Agent routing method|✔️|
|Presence-based routing|✔️|
|Opt out (queue configuration)|✔️|
|Opt agents in/out of queue|✔️|
|Routing for call overflow|✔️|
|Routing for call timeout|✔️|
|Routing for no agents|✔️|
|Real-time call queue metrics|✔️|
|Real-time agent metrics|✔️|
|Historical call queue metrics|✖️ Using Power BI<br>✔️ Using Customer Calls app|
|Historical agent metrics|✖️ Using Power BI<br>✔️ Using Customer Calls app|

For more information about these configuration features, see [Manage voice applications policies](manage-voice-applications-policies.md).

## Related topics

[Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)

[Manage voice applications policies](manage-voice-applications-policies.md)
