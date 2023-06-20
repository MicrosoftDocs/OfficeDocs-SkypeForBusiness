---
title: "Plan and configure Shared Calling"
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
description: "In this article, you'll learn about Phone System Shared Calling."
---

# Plan and configure Shared Calling

If you have users who are not heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number. 

For these users, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces cost for your organization because you don't need a dedicated phone number for every user.

With Shared Calling, instead of assigning a phone number to every user, you  assign a resource account number for an Auto attendant for outbound and inbound PSTN calls. Users have the same Phone System user experience and features, including the dial pad.

When a Shared Calling user makes an outbound call to the PSTN, the caller ID seen by recipients is that of the resource account number. You can also configure the resource account number as the callback number for your users.  

Auto attendants allow you to set up menu options to route calls based on caller input. For inbound calls to this number, the Auto attendant is used to route the call to the right person.

For more information about using Auto attendants, see [Plan for Auto attendants](plan-auto-attendant-call-queue.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

This article describes all the requirements for configuring Shared Calling.  You must ensure these requirements are met before creating a new [Shared Calling routing policy](shared-calling-setup.md).  

## Configuration requirements

- Each user must have a Phone System license assigned, and each user must be enabled for voice. To assign the license and enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the **EnterpriseVoiceEnabled** parameter to $true.

  For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md). 

- You must create a resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound calling is required, you must assign this resource account to a configured Auto attendant that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

- If the resource account is using a Calling Plan service number, you must assign a Calling Plan license to the resource account to enable outgoing minute billing. For more information, see [Manage resource accounts](manage-resource-accounts.md).

- If the resource account is using a Direct Routing phone number, for routing of outbound calls, you must configure a call routing policy and assign it to all users assigned to this resource account number. For more information, see [Manage call routing policies for Direct Routing](manage-voice-routing-policies.md). (This step is not required for resource accounts using a Calling Plan or Operator Connect number.)

- You must have Teams PowerShell Module version **NEED VERSION NUMBER**  to use the new -CsTeamsSharedCallingRoutingPolicy cmdlets. You'll use these cmdlets to create and manage Shared Calling policies. For more information, see [Configure Shared Calling policies](shared-calling-setup.md).

## Emergency calling requirements

You must ensure that users enabled for Shared Calling are able to make emergency calls. 

- You specify emergency call numbers by using the [emergency call routing policy](/powershell/module/skype/new-csteamsemergencycallroutingpolicy). You must create and assign an emergency call routing policy for each user enabled for Shared Calling--regardless of the type of number used for the resource account: Calling Plan, Operator Connect, or Direct Routing. However, if the resource account uses a Calling Plan or Operator Connect number, the emergency numbers should not have Online PSTN Usages assigned. For more information, see [Manage emergency call routing policies](manage-emergency-call-routing-policies.md).

- Emergency services must be able to call back to the originator of the emergency call. You can define a list of emergency callback numbers in the [Shared Calling routing policy](shared-calling-setup.md). If this list is empty, the phone number of the resource account is used as the emergency callback number.

- The emergency location provided to the emergency services is determined in the following order. Teams will first attempt to determine the actual location of the user. If that's not possible, it will default to the location specified in the [Shared Calling routing policy](shared-calling-setup.md): 

  1. Actual location of user -- dynamically obtained by the Teams client.
  2. Location assigned to the resource resource account specified in the Shared Calling routing policy -- statically obtained.

For more information about emergency calling and how location is determined, see  [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md#emergency-call-routing) and [Configure dynamic emerency calling](configure-dynamic-emergency-calling.md).

## Considerations

- Blocked caller ID might not work.
- What else?

## Related topics

- [Configure Shared Calling routing policies](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Configure dynamic emerency calling](configure-dynamic-emergency-calling.md)
- [What is Phone System](what-is-phone-system-in-office-365.md)
- [Phone System features](here-s-what-you-get-with-phone-system.md)