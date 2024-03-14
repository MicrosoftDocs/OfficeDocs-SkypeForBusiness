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
ms.date: 03/13/2024
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

Through **Authorized users**, you enable users in your organization—for example, business owners, team leads, supervisors of call queues--to manage day-to-day operational changes directly.

For example, authorized users can configure business hours, holiday greetings, and after hours call routing for Auto attendants and Call queues. For features only available with Teams Premium, authorized users can also configure business, after hours, and holiday call routing and they can view real-time and historical metrics for Auto attendants and Call queues all within the Queues app in the Teams client.

For a complete list of features, see [Manage voice applications policies](manage-voice-applications-policies.md).

## Licensing requirements

All Authorized users must have a Teams Phone license and must be "voice enabled". To assign the Teams Phone license, use the [Set-CsPhoneNumberAssignment](/powershell/set-csphonenumberassignment) cmdlet and set the `-EnterpriseVoiceEnabled` parameter to $true. For some configuration features, users must also have a Teams Premium license. For information about which features require Teams Premium, see [Manage voice applications policies](manage-voice-applications-policies.md).

For more information about assigning licenses, see [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md).

## Overview of steps for setting up authorized users

To create an authorized user, you must complete the following steps:  

- Step 1 - Assign licenses and enable users for voice  
- Step 2 - Assign phone numbers to your users
- Step 3 - Create a Teams voice applications policy
- Step 4 - Assign the voice applications policy to the user
- Step 5 - Create an Auto attendant or Call queue and assign licensed resource accounts
- Step 6 - Assign authorized users to the relevant Auto attendant or Call queue
- Step 7 - Set up the Customer Calls app for authorized users (optional)

For information on configuring these steps, see [Set up authorized users](aa-cq-authorized-users.md).

## What can authorized users configure

Configuration features for Auto attendants and Call queues are available to all authorized users with a Teams Phone license. However, some configuration features also require a Teams Premium license. For information about which features require Teams Premium, see [Manage voice applications policies](manage-voice-applications-policies.md).

### Auto attendants

You can delegate an authorized user to perform some or all of the following configuration tasks for Auto attendants:

| Feature | Teams Premium license required |
|-----------------------|--------------------------------|
|Business hours greeting||
|After hours greeting||
|Holiday greeting||
|Business hours|✔️|
|Holiday dates and hours|✔️|
|Business hours call routing|✔️|
|After hours call routing|✔️|
|Holiday hours call routing|✔️|
|Real-time auto attendant metrics|✔️|
|Historical auto attendant metrics in Power BI||
|Historical auto attendant metrics in Queues app|✔️|

For more information about these configuration features, see [Manage voice applications policies](manage-voice-applications-policies.md).

### Call queues

You can delegate an authorized user to perform some or all of the following configuration tasks for Call queues:

| Configuration feature | Teams Premium license required |
|-----------------------|--------------------------------|
|Welcome greeting||
|Music on Hold||
|Shared voicemail greeting for call overflow||
|Shared voicemail greeting for call timeout||
|Shared voicemail greeting for no agents||
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
|Historical call queue metrics in Power BI||
|Historical call queue metrics in Queues app|✔️|
|Historical agent metrics in Power BI||
|Historical agent metrics in Queues app|✔️|

For more information about these configuration features, see [Manage voice applications policies](manage-voice-applications-policies.md).

## Related topics

[Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)

[Manage voice applications policies](manage-voice-applications-policies.md)
