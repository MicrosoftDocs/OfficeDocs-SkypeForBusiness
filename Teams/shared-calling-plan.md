---
title: "Plan for Shared Calling"
ms.reviewer: jenstr
ms.date: 7/24/2023
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
ms.custom: 
  - Phone System
description: "In this article, you'll learn about Teams Phone Shared Calling."
---

# Plan for Shared Calling

If you have users who are not heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number.

For these users, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces cost for your organization because you don't need a dedicated phone number for every user.

With Shared Calling, instead of assigning a phone number to every user, you use the phone number of an Auto attendant for outbound and inbound PSTN calls.

- **Outbound calls.** When a Shared Calling user makes an outbound call to the PSTN, the caller ID seen by recipients is that of the Auto attendant.

- **Inbound calls.** When a Shared Calling user receives an inbound PSTN call, the call connects to the Auto attendant.

Auto attendants support multiple options for transferring a call to a user; for example, dial by name or dial by extension. Users have the same Teams Phone user experience and features, including the dial pad.

The Auto attendant phone number used is specified by the resource account associated with the Auto attendant.

For more information about using Auto attendants, see [Plan for Auto attendants](plan-auto-attendant-call-queue.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

This article describes all the requirements for configuring Shared Calling. You must ensure these requirements are met before creating a new [Shared Calling routing policy](shared-calling-setup.md).  

## Prerequisites

- Each user must have a Teams Phone license assigned, and each user must be "voice enabled." To assign the license, use the Microsoft 365 admin portal. To enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the **EnterpriseVoiceEnabled** parameter to $true. For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

- You must create a resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound calling is required, you must associate this resource account with a configured Auto attendant that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

- If the resource account is using a Calling Plan service number, you must have a [Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#pay-as-you-go-calling-plan) and fund it to enable outgoing minute billing and to support outbound calling from Shared Calling users.

- If the resource account is using a Direct Routing phone number, for routing of outbound calls, you must configure a call routing policy and assign it to all users assigned to the policy using this resource account number. For more information, see [Manage call routing policies for Direct Routing](manage-voice-routing-policies.md). This step is not required for resource accounts using a Calling Plan or Operator Connect number.

- You must have Teams PowerShell Module version 5.5.0 to use the new -CsTeamsSharedCallingRoutingPolicy cmdlets. You'll use these cmdlets to create and manage Shared Calling policies. For more information, see [Configure Shared Calling](shared-calling-setup.md).

- You must ensure that users enabled for Shared Calling are able to make emergency calls. For information, see [Configure Shared Calling](shared-calling-setup.md).

## Considerations

- Blocked caller ID might not work.

## Related topics

- [Configure Shared Calling](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
