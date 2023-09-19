---
title: "Configure Shared Calling"
ms.reviewer: jenstr
ms.date: 09/19/2023
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
description: "In this article, you'll learn how to configure Teams Phone Shared Calling routing policies."
---

# Configure Shared Calling

Before reading this article, be sure you've read [Plan for Shared Calling](shared-calling-plan.md). It describes licensing and other requirements needed to set up Shared Calling.

This article describes how to configure Shared Calling. You'll also need to set up your emergency call routing policy before creating Shared Calling.

For a step-by-step example on how to configure Shared Calling, see [Shared Calling scenario](shared-calling-scenario.md).

To associate a location on resource account number for Calling Plan, Operator Connect, and Direct Routing, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) PowerShell cmdlet.

## Configuration rules

- You can use the same resource account in multiple Shared Calling policies.
- All numbers within a given policy must be of the same number type and country (resource and emergency calling numbers).
- When you add a resource account to a policy, you must ensure that number has a location/emergency address assigned to it.
- If you remove, reassign, or port a number of the resource account used in a shared calling policy, the policy remains intact, but outbound calls will fail for any users still configured to make calls from that number.

## Emergency calling for Shared Calling users

Shared Calling users need to be able to make emergency calls to the emergency services. In order to do so, the following 3 things need to be configured:

1. **[Emergency service number](#configure-emergency-service-numbers)**: The Teams client used by the Shared Calling user needs to recognize that a given phone number called is an emergency service number like 911. This is done by configuring the Emergency call routing policy.
1. **[Emergency callback number](#emergency-callback-number)**: The emergency services need to be able to call back to a user that have dialed the emergency services. Since a Shared Calling user does not have a dedicated phone number assigned, either the phone number of the resource account or configured emergency numbers will be used.
1. **[Emergency location](#emergency-location)**: The emergency services need to be make aware of the location or emergency address of the Shared Calling user making the emergency call.

### Configure emergency service numbers

Emergency service numbers are defined in the emergency call routing policy. If you've not already done so, you must create and assign an emergency call routing policy for each user enabled for Shared Calling--regardless of the type of number used for the resource account: Calling Plan, Operator Connect, or Direct Routing.

In some Calling Plan markets, you aren't allowed to set the location on service numbers. For these markets, please contact the [Telephone Number Services service desk](phone-reference/manage-numbers/contact-tns-service-desk.md).

If you are attempting to use a resource account with an Operator Connect phone number assigned, you should confirm support for Shared Calling with your operator.

Shared Calling isn't supported for Calling Plan service phone numbers in Romania, the Czech Republic, Hungary, Singapore, New Zealand, Australia, and Japan. A limited number of existing Calling Plan service phone numbers in other countries are also not supported for Shared Calling. For information about these service phone numbers, please contact the [Telephone Number Services service desk](phone-reference/manage-numbers/contact-tns-service-desk.md).

### Routing of emergency calls

The routing of the emergency call is based on how the resource account is configured. If the resource account used in the Shared Calling policy uses a Calling Plan or Operator Connect number, the emergency call routing policy assigned to the Shared Calling user shouldn't have online PSTN usages configured. If the emergency call routing policy used for the emergency call has online PSTN usages configured, the routing of the emergency call will be based on the online PSTN usages. For more information, see [Manage emergency call routing policies](manage-emergency-call-routing-policies.md) and [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage).

### Emergency callback number

Emergency services must be able to call back the originator of the emergency call. The phone number used for this is called an *emergency callback number* and this number will act as the caller ID or calling number used when an emergency call is made.

You aren't required to define emergency numbers for a Shared Calling policy. If you don't define emergency numbers, when an emergency call is made, the number associated with the resource account in the Shared Calling policy is used.

You can define a list of emergency callback numbers in the -EmergencyNumbers parameter of the Shared Calling routing policy. Each Shared Calling policy must have a unique emergency calling number. That is, you can't use the same emergency number in more than one Shared Calling policy.

When an emergency call is made, the next free number in the emergency number list will be used as the caller ID and this number will be reserved for the next 60 minutes.

- If there are no free numbers available in the list, we will reuse a phone number from the list.
- If this list is empty, the phone number of the resource account is used as the emergency callback number--however, this isn't supported if your resource account is assigned a Calling Plan toll free service number.

When emergency numbers are added to a policy:

- The emergency numbers must be routable for inbound PSTN calls. For Calling Plan & Operator Connect, the callback numbers must be available within the tenant.
- The emergency numbers specified must all be of the same phone number type as the phone number assigned to the specified resource account--that is Calling Plan, Operator Connect, or Direct Routing.
- The emergency numbers can’t be assigned to any user or resource account

You can't delete or reassign an emergency number used in any Shared Calling policy. You must first remove the number from the Shared Calling policy before you delete or reassign the number.

You can view all Calling Plan and Operator Connect emergency numbers by country, number sequence, or policy group by using the Teams admin center. For assigned Direct Routing numbers, you can use [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) -NumberType DirectRouting.

#### Calling Plan service numbers

- If the resource account has assigned a Calling Plan service number, then the emergency callback number must be a Calling Plan subscriber number--not a Calling Plan service number.
- If your resource account is assigned a Calling Plan toll-free service number, you need to add Calling Plan subscriber numbers to emergency numbers in the policy.

### Emergency location

The emergency location provided to the emergency services via the emergency call is determined in the following order.

Teams will first attempt to dynamically determine the actual location of the user. If that's not possible, it will default to the location defined on the phone number of the resource account specified in the Shared Calling routing policy:

1. Actual location of user -- dynamically obtained by the Teams client.
1. Location assigned to the phone number assigned to the resource account specified in the Shared Calling routing policy -- statically obtained.

For more information about emergency calling and how location is determined, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

Emergency calling for Shared Calling is available globally. There are configuration requirements for customers outside of North America. You need to ensure that the emergency addresses assigned to the phone numbers used for the resource accounts in the Shared Calling policy instances are uploaded to their carrier’s emergency calling database.

## Shared Calling routing policy

Once you've created your emergency call routing policy, you'll create your Shared Calling routing policy.

To configure and manage Shared Calling routing policies, you'll use the following Teams PowerShell cmdlets:

- [New-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/new-csteamssharedcallingroutingpolicy)
- [Get-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/get-csteamssharedcallingroutingpolicy)
- [Remove-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/remove-csteamssharedcallingroutingpolicy)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Grant-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/grant-csteamssharedcallingroutingpolicy)

For example, the following command creates a new Shared Calling policy, called Seattle, and configures the policy with the resource account main-aa@contoso.com. The command also identifies the emergency callback numbers associated with the resource account:

```powershell
$ecbn1 = '+14255556789'
$ecbn2 = '+14255554321'
$ra = Get-CsOnlineUser -Identity main-aa@contoso.com
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

For more examples on configuring Shared Calling policies, see [Shared Calling scenario](shared-calling-scenario.md).

## Related topics

- [Plan for Shared Calling](shared-calling-plan.md)
- [Shared Calling scenario](shared-calling-scenario.md)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)
