---
title: "What is Shared Calling"
ms.reviewer: roykuntz
ms.date: 5/30/2023
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-apr2020
  - intro-overview
description: "In this article, you'll learn about Teams Phone Shared Calling."
---

# What is Shared Calling

If you have users who are not heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number. 

With Shared Calling, instead of assigning a phone number to every user, you can assign a resource account number (for an Auto Attendant or Call Queue) for outbound and inbound PSTN calls. Users use the resource account number to make outgoing calls. You can also configure the resource acct number as the callback number for your users. Users have the same Phone System user experience and features (true?), including the dial pad. (For more information about Phone System features, see [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)).

For example, if you want all users to call out using the same number, you can use a resource account with an Auto Attendant.  If the call-out number is a service desk or help desk, you can use a resource account with a Call Queue.  When a user makes an outbound call, the number shown to the recipient will be that of the Auto Attendant or Call Queue. When the recpient calls back, the call is managed by the Auto Attendant or Call Queue.

For users who do not need a dedicated assigned phone number, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces cost for your organization because you don't need a calling plan license for every user.

## Requirements

- Each user must have a Phone System license assigned, and each user must be enabled for voice. 

  For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md). 
  
  To assign the license and enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the **EnterpriseVoiceEnabled** parameter to $true.

- You must create a resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound PSTN calling is required, you must assign this resource account to a configured Auto Attendant or Call Queue that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md), [Set up an auto attendant](create-a-phone-system-auto-attendant.md) and [Set up a call queue](create-a-phone-system-call-queue.d).

- If the resource account is using a Calling Plan service number, you must assign a Calling Plan license to the resource account to enable outgoing minute billing. For more information, see [Manage resource accounts](manage-resource-accounts.md).

- You must have Teams PowerShell Module version ??  to use the new -CsTeamsSharedCallingRoutingPolicy cmdlets.  You will use these cmdlets to create and manage Shared Calling policies.  For more information, see [Set up Shared Calling](set-up-shared-calling.md).



- You must create and assign an emergency call routing policy for each user. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md#emergency-call-routing) and [Considerations for PSTN connectivity options](what-are-emergency-locations-addresses-and-call-routing.md#considerations-for-pstn-connectivity-options).

## Considerations

- Blocked caller ID might not work.

## Related topics

- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Shared Calling](set-up-shared-calling.md)
- [Set up an auto attendant](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [What is Phone System](what-is-phone-system-in-office-365.md)
- [Phone System features](here-s-what-you-get-with-phone-system.md)