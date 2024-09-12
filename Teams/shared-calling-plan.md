---
title: "Plan for Shared Calling"
ms.reviewer: roykuntz, jastark
ms.date: 09/12/2024
author: mkbond007
ms.author: mabond
manager: pamgreen
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

This article describes what you need to know before configuring Shared Calling for Teams Phone.

If you have users who aren't heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number. Instead, for these users, you should consider Shared Calling as a simpler, easier-to-implement phone solution for your organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces costs for your organization because you don't need a dedicated phone number for every user. Optionally, you can also configure extension dialing support for Shared Calling users.

Note: Shared Calling is currently available in public clouds only.

Let's start with some definitions that you need to know for Shared Calling:

| Term | Definition |
|----------|-----------|
|Auto attendant|Directs a caller to an appropriate person or department based on the caller's input to the provided menu options--for example, dial by name. The Auto attendant phone number used is specified by the resource account associated with the Auto attendant.<br><br>For more information about using Auto attendants, see [Plan for Auto attendants](plan-auto-attendant-call-queue.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).|
|Inbound calls|An incoming call that comes from a PSTN to a user in your organization. When a Shared Calling user receives an inbound PSTN call, the call connects to the Auto attendant.|
|Outbound calls|An outgoing call by a user in your organization to a PSTN. When a Shared Calling user makes an outbound call to the PSTN, the recipients see the caller ID of the Auto attendant.|

With Shared Calling, instead of assigning a phone number to every user, you use the phone number of a resource account associated with an Auto attendant for inbound and outbound PSTN calls. The Shared Calling policy configures the resource account used for outbound calls and emergency numbers that are used as emergency callback numbers.

To set up Shared Calling, you need to perform the following steps. These steps are described in detail in [Configure Shared Calling](shared-calling-setup.md).

1. Assign Teams Phone licenses and enable users for voice. Don't assign a phone number to any Shared Calling enabled user.

1. Assign number to resource account for inbound and outbound calling.

1. Associate resource account with Auto attendant for inbound calling.

1. Assign a location to the resource account for emergency calling.

1. Configure resource accounts with service numbers. Communication Credits might be required if your tenant doesn't have the New commerce experience calling subscriptions, or you don't want to post pay for calls.

1. Create voice routing policy without PSTN usages.

1. Enable emergency calling for users.

1. Create your Shared Calling policy.

1. Assign the Shared Calling policy to users.

1. Configure extension dialing support for Shared Calling enabled users (optional).

Shared Calling can be configured with the Teams admin center and PowerShell. You must have Teams PowerShell Module version 5.5.0 or higher to use the new [TeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy) cmdlets. You can use these cmdlets to create and manage Shared Calling policies.

## Related articles

- [Configure Shared Calling](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
