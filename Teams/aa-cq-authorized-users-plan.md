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
ms.date: 10/22/2024
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

All Authorized users must have a Teams Phone license and must be "voice enabled." To assign the Teams Phone license, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet and set the `-EnterpriseVoiceEnabled` parameter to $true.

For some configuration features, such as those available only in the Queues app, users must also have a Teams Premium license. For information about which features require Teams Premium, see [Manage voice applications policies](manage-voice-applications-policies.md).

For more information about assigning licenses, see [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md).

## Overview of steps for setting up authorized users

To create an authorized user, you must complete the following steps:  

- Step 1 - Assign licenses and enable users for voice  
- Step 2 - Assign phone numbers to your users
- Step 3 - Create a Teams voice applications policy
- Step 4 - Assign the voice applications policy to the user
- Step 5 - Create an Auto attendant or Call queue and assign licensed resource accounts
- Step 6 - Assign authorized users to the relevant Auto attendant or Call queue
- Step 7 - Set up the Queues app for authorized users (optional)

For information on configuring these steps, see [Set up authorized users](aa-cq-authorized-users.md).

## Related topics

[Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)

[Manage voice applications policies](manage-voice-applications-policies.md)

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)
