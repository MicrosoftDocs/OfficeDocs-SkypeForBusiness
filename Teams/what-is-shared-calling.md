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

With Shared Calling, instead of assigning a phone number to every user, you can assign a resource account number (for an Auto Attendant or Call Queue) for outbound and inbound PSTN calls. Users have the same Phone System user experience and features, including the dial pad.

When a Shared Calling user makes an outbound call to the PSTN, the caller ID seen by recipients is that of the resource account number. You can also configure the resource account number as the callback number for your users.  

For example, if you want all users to call out using the same number, you can use a resource account with an Auto Attendant. Auto attendants allow you to set up menu options to route calls based on caller input. For inbound calls to this number, the Auto Attendant is used to route the call to the right person.

If the call-out number is for a service desk or help desk, you can use a resource account with a Call Queue. Call queues connect callers to the group of agents who can assist them. For inbound calls, callers are put on hold until an agent assigned to the queue is available to take their call.

For users who do not need a dedicated assigned phone number, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces cost for your organization because you don't need a calling plan license for every user.

For more information about using Auto Attendants and Call Queues, see [Plan for Auto Attendants and Call Queues](plan-auto-attendant-call-queue.md).

## Requirements

- Each user must have a Phone System license assigned, and each user must be enabled for voice. To assign the license and enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the **EnterpriseVoiceEnabled** parameter to $true.

  For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md). 

- You must create a resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound calling is required, you must assign this resource account to a configured Auto Attendant or Call Queue that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md), [Set up an auto attendant](create-a-phone-system-auto-attendant.md) and [Set up a call queue](create-a-phone-system-call-queue.d).

- If the resource account is using a Calling Plan service number, you must assign a Calling Plan license to the resource account to enable outgoing minute billing. For more information, see [Manage resource accounts](manage-resource-accounts.md).

- If the resource account is using a Direct Routing phone number, for routing of outbound calls, you must configure an Online Voice Routing Policy and assign it to all users assigned to this resource account number.  (This step is not required for resource accounts using a Calling Plan or Operator Connect number.)

- You must have Teams PowerShell Module version ??  to use the new -CsTeamsSharedCallingRoutingPolicy cmdlets.  You will use these cmdlets to create and manage Shared Calling policies.  For more information, see [Set up Shared Calling](set-up-shared-calling.md).

## Emergency calling requirements

You must ensure that users enabled for Shared Calling are able to make emergency calls. 

- You specify emergency call numbers by using the emergency call routing policy. You must assign this policy to each user enabled for Shared Calling. If the resource account used has an Operator Connect or Calling Plan number assigned, the emergency numbers should not have Online PSTN Usages assigned.

- Emergency services must be able to call back to the originator of the emergency call. You can define a list of emergency callback numbers in the Shared Calling routing policy. If this list is empty, the phone number of the resource account is used as the emergency callback number.

- The emergency location provided to the emergency services is determined by one of the following:   **DO WE NEED TO GIVE MORE INFO ABOUT WHEN IT'S ONE OR THE OTHER?**

  - Dynamically obtained by the Teams client based on the actual location of the user.
  - Statically obtained from the location assigned to the resource account specified in the Shared Calling routing policy.

- If a Shared Calling user is using a resource account with a Direct Routing phone number assigned, for routing of outbound calls, you must configure an Online Voice Routing Policy and assign it to the user.  (This step is not required for resource accounts using a Calling Plan or Operator Connect number.)

For more information about emergency calling, see  [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md#emergency-call-routing) and [Considerations for PSTN connectivity options](what-are-emergency-locations-addresses-and-call-routing.md#considerations-for-pstn-connectivity-options).

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