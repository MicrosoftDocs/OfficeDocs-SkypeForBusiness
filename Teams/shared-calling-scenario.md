---
title: "Shared Calling scenario"
ms.reviewer: roykuntz
ms.date: 09/20/2023
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
description: "This article provides a Shared Calling example scenario."
---

# Shared Calling example scenario

Before reading this article, be sure you've read [Plan for Shared Calling](shared-calling-plan.md) and [Configure Shared Calling](shared-calling-setup.md). These articles describe licensing requirements, prerequisite configuration, and how to configure a Shared Calling policy.

This article provides a sample scenario for setting up Shared Calling. It provides a PowerShell example for the following steps:

1. Get the Shared Calling user.
1. Enable voice for the user.
1. Get the phone number of the Auto attendant resource account.
1. Create the emergency call routing policy based on the phone number type of the Auto attendant.
1. Set the static emergency location on the resource account.
1. Create the Shared Calling policy.
1. Grant the Shared Calling policy to the user.

## Shared Calling PowerShell example

```powershell
# Get the Shared Calling user
$user = Get-CsOnlineUser -Identity user@contoso.com

## Enable voice for the user
Set-CsPhoneNumberAssignment -Identity user@contoso.com -EnterpriseVoiceEnabled $true

## Get the phone number of the Auto attendant resource account
$mainaa = 'main-aa@contoso.com'
$PhoneNumber=Get-CsPhoneNumberAssignment -AssignedPstnTargetId $mainaa

if ($PhoneNumber.NumberType -eq 'DirectRouting') {
    # Define the emergency numbers for emergency calling
    $en1=New-CsTeamsEmergencyNumber -EmergencyDialString 933 -OnlinePSTNUsage WW
    $en2=New-CsTeamsEmergencyNumber -EmergencyDialString 911 -OnlinePSTNUsage WW

    New-CsTeamsEmergencyCallRoutingPolicy -Identity TECRP-DR -EmergencyNumbers @{add=$en1,$en2} -AllowEnhancedEmergencyServices $true

    # Grant the policy to the user
    Grant-CsTeamsEmergencyCallRoutingPolicy -Identity $user -PolicyName TECRP-DR
}

else {
    # Define the emergency numbers for emergency calling
    $en1=New-CsTeamsEmergencyNumber -EmergencyDialString 933
    $en2=New-CsTeamsEmergencyNumber -EmergencyDialString 911

    New-CsTeamsEmergencyCallRoutingPolicy -Identity TECRP-CPOC -EmergencyNumbers @{add=$en1,$en2} -AllowEnhancedEmergencyServices $true

    # Grant the policy to the user
    Grant-CsTeamsEmergencyCallRoutingPolicy -Identity $user -PolicyName TECRP-CPOC
}

# Set the static emergency location on the resource account
$CivicAddress = Get-CsOnlineLisCivicAddress -City Seattle
Set-CsPhoneNumberAssignment -LocationId $CivicAddress.DefaultLocationId -PhoneNumber $PhoneNumber.TelephoneNumber

# Create the Shared Calling policy
$ecbn1 = '+14255556789'
$ecbn2 = '+14255554321'
$ra = Get-CsOnlineUser -Identity $mainaa
New-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -ResourceAccount $ra.Identity -EmergencyNumbers @{add=$ecbn1,$ecbn2}

# Grant the Shared Calling policy to the user
Grant-CsTeamsSharedCallingRoutingPolicy -Identity $user -PolicyName Seattle
```

## Related topics

- [Plan for Shared Calling](shared-calling-plan.md)
- [Configure Shared Calling policies](shared-calling-setup.md)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
