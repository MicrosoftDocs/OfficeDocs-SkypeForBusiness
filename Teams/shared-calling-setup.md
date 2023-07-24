---
title: "Configure Shared Calling"
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
description: "In this article, you'll learn how to configure Teams Phone Shared Calling policies."
---

# Configure Shared Calling

Before reading this article, be sure you've read [Plan for Shared Calling](shared-calling-plan.md). It describes licensing and other requirements needed to set up Shared Calling.

This article describes how to configure Shared Calling. You'll also need to set up your emergency call routing policy before creating Shared Calling.

For a step-by-step example on how to configure Shared Calling, see [Shared Calling scenario](shared-calling-scenario.md).

## Shared Calling routing policy

To configure and manage Shared Calling routing policies, you'll use the following Teams PowerShell cmdlets:

- [New-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/new-csteamssharedcallingroutingpolicy)
- [Get-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/get-csteamssharedcallingroutingpolicy)
- [Remove-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/remove-csteamssharedcallingroutingpolicy)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Grant-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/grant-csteamssharedcallingroutingpolicy)

For example, the following command creates a new Shared Calling policy, called Seattle, and assigns it to resource account main-add@contoso.com. The command also identifies the emergency callback numbers associated with the resource account:

```powershell
$ecbn1 = '+14255556789'
$ecbn2 = '+14255554321'
$ra = Get-CsOnlineUser -Identity main-add@contoso.com
New-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -ResourceAccount $ra.Identity -EmergencyNumbers @{add=$ecbn1,$ecbn2}

```

The next command removes one of the emergency callback numbers, +14255554321, from the policy (required before that number can be deleted or reassigned):

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -EmergencyNumbers @{remove='+14255554321'} 
```

The next command adds a new emergency callback number, 1425555433, to the policy:

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -EmergencyNumbers @{add='+1425555433'} 
```

To associate a location on resource account number for Calling Plan, Operator Connect, and Direct Routing, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet.

### Configuration rules

- You can use the same resource account in multiple Shared Calling policies.

- All numbers within a given policy must be of the same number type and country (resource and emergency calling numbers).

- When you add a resource account to a policy, you must ensure that number has a location assigned to it.

- If you remove, reassign, or port a number of the resource account used in a Shared Calling policy, the policy remains intact, but outbound calls will fail for any users still configured to make calls from that number.

## Emergency calling routing policy

If you've not already done so, you must create and assign an emergency call routing policy for each user enabled for Shared Calling--regardless of the type of number used for the resource account: Calling Plan, Operator Connect, or Direct Routing. You can specify emergency numbers by using the [emergency call routing policy](/powershell/module/skype/new-csteamsemergencycallroutingpolicy).

If the resource account uses a Calling Plan or Operator Connect number, the emergency numbers defined in the emergency call routing policy shouldn't have Online PSTN Usages assigned. For more information, see [Manage emergency call routing policies](manage-emergency-call-routing-policies.md).

Emergency calling for Shared Calling is available globally. There are configuration requirements for customers outside of North America. You need to ensure that the emergency addresses assigned to the phone numbers used for the resource accounts in the Shared Calling policy instances are uploaded to their carriers emergency calling database.

### Emergency callback number

Emergency services must be able to call back the originator of the emergency call. The phone number used for this is called an *emergency callback number* and this number will act as the caller ID or calling number used when an emergency call is made.

You can define a list of emergency callback numbers in the EmergencyNumbers parameter of the [Shared Calling routing policy](shared-calling-setup.md). Each Shared Calling policy must have a unique emergency calling number. That is, you can't use the same emergency number in more than one Shared Calling policy.

You aren't required to define emergency numbers for a Shared Calling policy. If you don't define emergency numbers, when an emergency call is made, the number associated with the resource account in the policy is used. You can assign emergency addresses to resource account numbers.

When an emergency call is made, the next free number in the emergency number list will be used as the caller ID and this number will be reserved for the next 60 minutes.

- If there are no free numbers available in the list, we will reuse a phone number from the list.

- If this list is empty, the phone number of the resource account is used as the emergency callback number--however, this isn't supported if your resource account is assigned a Calling Plan toll free service number.

When emergency numbers are added to a policy:

- Only the location from the resource account will be used--emergency numbers don't require an associated location.

- The emergency numbers must be routable for inbound PSTN calls. For Calling Plan & Operator Connect, the callback numbers must be available within the tenant.

- The emergency numbers specified must all be of the same phone number type as the phone number assigned to the specified resource account--that is Calling Plan, Operator Connect, or Direct Routing.

You can't delete or reassign an emergency number used in any Shared Calling policy. You must first remove the number from the Shared Calling policy before you delete or reassign the number.

You can view all Calling Plan and Operator Connect emergency numbers by country, number sequence, or policy group by using the Teams admin center. For assigned Direct Routing numbers, you can use Get-CsPhoneNumberAssignment -NumberType DirectRouting.

#### Calling Plan service numbers

- If the resource account has assigned a Calling Plan service number, then the emergency callback number must be a Calling Plan subscriber number--not a Calling Plan service number.

- If your resource account is assigned a Calling Plan toll-free service number, you need to add Calling Plan subscriber numbers to emergency numbers in the policy.

### Emergency location

The emergency location provided to the emergency services is determined in the following order. Teams will first attempt to determine the actual location of the user. If that's not possible, it will default to the location specified in the [Shared Calling routing policy](shared-calling-setup.md):

  1. Actual location of user -- dynamically obtained by the Teams client.
  2. Location assigned to the phone number assigned to the resource account specified in the Shared Calling routing policy -- statically obtained.

For more information about emergency calling and how location is determined, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md#emergency-call-routing) and [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Related topics

- [Plan for Shared Calling](shared-calling-plan.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
