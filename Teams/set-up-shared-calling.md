---
title: "Set up Shared Calling"
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
description: "In this article, you'll learn how to configure Teams Phone Shared Calling."
---

# Set up Shared Calling

Before reading this article, be sure you've read [What is Shared Calling](what-is-shared-calling.md). It describes licensing and other requirements needed to configure Shared Calling.

To set up and manage Shared Calling, you'll use the following Teams PowerShell cmdlets: 

**NOTE TO ME:  Add links to reference topics**
- New-CsTeamsSharedCallingRoutingPolicy
- Get-CsTeamsSharedCallingRoutingPolicy
- Remove-CsTeamsSharedCallingRoutingPolicy 
- Set-CsTeamsSharedCallingRoutingPolicy 
- Grant-CsTeamsSharedCallingRoutingPolicy

For example, the following command creates a new Shared Calling policy, called Test, and assigns it to resource account ra1@contose.com. The command also identifes the emergency callback numbers associated with the resource account: 

```powershell
New-CsTeamsSharedCallingRoutingPolicy -Identity Test -ResourceAccount ra1@contoso.com -EmergencyCallbackNumbers {@add='+12065556677','+14255556677','+1425555432'} 
```

The next command removes one of the emergency callback numbers, 1425555432, from the policy (required before that number can be deleted or reassigned):

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Test -EmergencyCallbackNumbers {@remove='+1425555432'} 
```

The next command adds a new emergency callback number, 1425555433, to the policy:

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Test -EmergencyCallbackNumbers {@add='+1425555433'} 
```

To associate a location on resource account numbers for Calling Plan, Operator Connect, and Direct Routing, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet.

## Configuration rules

- You can use the same resource account in multiple Shared Calling policies.

- All numbers within a given policy must be of the same number type and country (resource and emergency calling numbers). 

- When you add a resource account to a policy, you must ensure that number has a location assigned to it.

- If you remove, reassign, or port a number of the resource account used in a shared calling policy, the policy remains intact, but outbound calls will fail for any users still configured to make calls from that number.

## Emergency calling rules

- You are not required to define emergency numbers for a Shared Calling policy. If you don't define emergency numbers, when an emergency number is made, the resource account in the policy is used. (You can assign emergency addresses to resource account numbers.)

- Each Shared Calling policy must have unique emergency calling number(s). That is, you can't use the same emergency number in more than one Shared Calling policy. 

- When emergency callback numbers are added to a policy: 

  - Callback numbers do not require an associated location--only the location from the resource account will be used.

  - You can view all Calling Plan and Operator Connect emergency numbers by country, number sequence, or policy group by using the Teams admin center.  For Direct Routing numbers...  (TAC doesn’t show DR numbers so need to define how to deal with this) 

  - You can't delete or reassign an emergency number used in any Shared Calling policy. You must first remove the number from the Shared Calling policy before you delete or reassign the number. 



## Related topics

- [What is Shared Calling](what-is-shared-calling.md)
- [Set up an auto attendant](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
