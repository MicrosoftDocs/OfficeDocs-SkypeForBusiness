---
title: "Plan and configure Shared Calling"
ms.reviewer: jenstr
ms.date: 7/21/2023
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
description: "In this article, you'll learn about Phone System Shared Calling."
---

# Plan and configure Shared Calling

If you have users who are not heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number.

For these users, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces cost for your organization because you don't need a dedicated phone number for every user.

With Shared Calling, instead of assigning a phone number to every user, you use the phone number of an Auto attendant for outbound and inbound PSTN calls.

- **Outbound calls.** When a Shared Calling user makes an outbound call to the PSTN, the caller ID seen by recipients is that of the Auto attendant.

- **Inbound calls.** When a Shared Calling user receives an inbound PSTN call, the call connects to the Auto attendant.

Auto attendants support multiple options for transferring a call to a user; for example, dial by name or dial by extension. Users have the same Phone System user experience and features, including the dial pad.

The Auto Attendant phone number used is specified by the resource account associated with the Auto Attendant.

For more information about using Auto attendants, see [Plan for Auto attendants](plan-auto-attendant-call-queue.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

This article describes all the requirements for configuring Shared Calling. You must ensure these requirements are met before creating a new [Shared Calling routing policy](shared-calling-setup.md).  

## Configuration requirements

- Each user must have a Phone System license assigned, and each user must be enabled for Enterprise Voice. To assign the license, use the Microsoft 365 admin portal. To enable users for Enterprise Voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps), and set the **EnterpriseVoiceEnabled** parameter to $true.

  For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

- You must create a resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

- If inbound calling is required, you must associate this resource account with a configured Auto attendant that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

- If the resource account is using a Calling Plan service number, you must have a [Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#pay-as-you-go-calling-plan) and fund it to enable outgoing minute billing and to support outbound calling from Shared Calling users.

- If the resource account is using a Direct Routing phone number, for routing of outbound calls, you must configure a call routing policy and assign it to all users assigned to the policy using this resource account number. For more information, see [Manage call routing policies for Direct Routing](manage-voice-routing-policies.md). This step is not required for resource accounts using a Calling Plan or Operator Connect number.

- You must have Teams PowerShell Module version 5.5.0 to use the new -CsTeamsSharedCallingRoutingPolicy cmdlets. You'll use these cmdlets to create and manage Shared Calling policies. For more information, see [Configure Shared Calling policies](shared-calling-setup.md).

## Emergency calling requirements

As an admin, you must ensure that users enabled for Shared Calling are able to make emergency calls.

You must create and assign an emergency call routing policy for each user enabled for Shared Calling--regardless of the type of number used for the resource account: Calling Plan, Operator Connect, or Direct Routing. You can specify emergency numbers by using the [emergency call routing policy](/powershell/module/skype/new-csteamsemergencycallroutingpolicy).

If the resource account uses a Calling Plan or Operator Connect number, the emergency numbers defined in the emergency call routing policy shouldn't have Online PSTN Usages assigned. For more information, see [Manage emergency call routing policies](manage-emergency-call-routing-policies.md).

Emergency calling for Shared Calling is available globally. There are configuration requirements for customers outside of North America. You need to ensure that the emergency addresses assigned to the phone numbers used for the resource accounts in the Shared Calling policy instances are uploaded to their carriers emergency calling database.

### Emergency callback number

Emergency services must be able to call back the originator of the emergency call. The phone number used for this is called an *emergency callback number* and this number will act as the caller id or calling number used when an emergency call is made.

You can define a list of emergency callback numbers in the EmergencyNumbers parameter of the [Shared Calling routing policy](shared-calling-setup.md).

- When an emergency call is made, the next free number in the emergency number list will be used as the caller id and this number will be reserved for the next 60 minutes.

- If there are no free numbers available in the list, we will reuse a phone number from the list.

- If this list is empty, the phone number of the resource account is used as the emergency callback number--however, this isn't supported if your resource account is assigned a Calling Plan toll free service number.

- The emergency numbers specified must all be of the same phone number type as the phone number assigned to the specified resource account--that is Calling Plan, Operator Connect, or Direct Routing.

- If the resource account has assigned a Calling Plan service number, then the emergency callback number(s) must be Calling Plan *subscriber* number(s)--not Calling Plan service number(s).

- If your resource account is assigned a Calling Plan toll-free service number, you need to add Calling Plan subscriber numbers to emergency numbers in the policy.

### Emergency location

The emergency location provided to the emergency services is determined in the following order. Teams will first attempt to determine the actual location of the user. If that's not possible, it will default to the location specified in the [Shared Calling routing policy](shared-calling-setup.md):

  1. Actual location of user -- dynamically obtained by the Teams client.
  2. Location assigned to the phone number assigned to the resource resource account specified in the Shared Calling routing policy -- statically obtained.

For more information about emergency calling and how location is determined, see  [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md#emergency-call-routing) and [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Considerations

- Blocked caller ID might not work.

## Related topics

- [Configure Shared Calling routing policies](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [What is Phone System](what-is-phone-system-in-office-365.md)
- [Phone System features](here-s-what-you-get-with-phone-system.md)
