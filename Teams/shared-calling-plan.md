---
title: "Plan for Shared Calling"
ms.reviewer: jenstr
ms.date: 09/14/2023
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

To allow emergency services to call back Shared Calling users who've made emergency calls, you can configure one or more emergency numbers.

This article describes all the prerequisites for configuring Shared Calling using the Shared Calling routing policy. The Shared Calling routing policy configures the resource account used for outbound calls and emergency numbers that will be used as emergency call back numbers.

You must ensure these requirements are met before creating a new [Shared Calling routing policy](shared-calling-setup.md).  

## Prerequisites

- Each user must have a Teams Phone license assigned, and each user must be "voice enabled." To assign the license, use the Microsoft 365 admin portal. To enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the -EnterpriseVoiceEnabled parameter to $true. For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

- You must create or reuse an existing resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound calling is required, you must associate this resource account with a configured Auto attendant that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

- If the resource account is using a Calling Plan service number, you must have a [Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#pay-as-you-go-calling-plan), and assign it to the resource account. In addition, you need to assign a Communications credits license to the resource account and fund it to support outbound Shared Calling calls via the Pay-As-You-Go Calling Plan. For more information, see [How to fund a Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#how-to-fund-a-pay-as-you-go-calling-plan), [Enable pay-as-you-go for your subscription](/microsoft-365/commerce/subscriptions/manage-pay-as-you-go-services.md), [Customers with new commerce experience calling subscriptions](what-are-communications-credits.md#customers-with-new-commerce-experience-calling-subscriptions) and [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

- Shared Calling users must not have an assigned Voice Routing Policy with valid PSTN usages. If you are using Global Voice Routing Policies in your tenant with valid PSTN usages, then you must create a new Online Voice Routing Policy with empty PSTN usages and assign this policy to Shared Calling users.

- You must have Teams PowerShell Module version 5.5.0 to use the new TeamsSharedCallingRoutingPolicy cmdlets. You'll use these cmdlets to create and manage Shared Calling policies. For more information, see [Configure Shared Calling](shared-calling-setup.md).

- You must ensure that users enabled for Shared Calling are able to make emergency calls. For information, see [Configure Shared Calling](shared-calling-setup.md).

## Related topics

- [Configure Shared Calling](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
