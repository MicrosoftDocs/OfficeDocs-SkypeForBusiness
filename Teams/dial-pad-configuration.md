---
title: Teams dial pad configuration
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: cbland
ms.date: 05/21/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: "Learn about how to configure the dial pad in the Teams client so that users can access Public Switched Telephone Network (PSTN) functionality."
---

# Dial pad configuration

In the Teams client, the dial pad enables users to access Public Switched Telephone Network (PSTN) functionality. The dial pad is available for users with a Teams Phone license, provided they're configured properly. The following criteria are all required for the dial pad to show:

- User has an enabled Teams Phone ("MCOEV") license
- User is homed online and not in Skype for Business on premises
- User has Enterprise Voice enabled
- User has Allow Private Calling enabled in Teams Calling Policy

To successfully place a call using the dial pad, the user must have one of the following:  Microsoft Calling Plan, Operator Connect, is enabled for Direct Routing, or is able to use Shared Calling. For more information about Shared Calling, see [Plan for Shared Calling](shared-calling-plan.md).

The following sections describe how to use PowerShell to check the criteria. In most cases, you need to look at various properties in the output of the [Get-CsOnlineUser](/powershell/module/teams/get-csonlineuser) cmdlet. Examples assume $user is either the UPN (UserPrincipalName) or SIP address of the user.

## User has an enabled Teams Phone ("MCOEV") license

Make sure that the assigned plan for the user shows the **CapabilityStatus attribute set to Enabled** and the **Capability set to MCOEV** (Teams Phone license). You might see MCOEV, MCOEV1, and so on. All are acceptable--as long as the Capability starts with MCOEV. For more information on the Teams Phone license, see [Microsoft Teams add-on licensing](/MicrosoftTeams/teams-add-on-licensing/assign-teams-add-on-licenses).

To check that the attributes are set correctly, use the following command:

```PowerShell
(Get-CsOnlineUser -Identity $user).AssignedPlan
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability** attributes:

```PowerShell
AssignedTimestamp   Capability      CapabilityStatus ServiceInstance                          ServicePlanId
-----------------   ----------      ---------------- ---------------                          -------------
07-02-2020 12:28:48 MCOEV           Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 4828c8ec-dc2e-4779-b502-...
07-02-2020 12:28:48 Teams           Enabled          TeamspaceAPI/NA001                       57ff2da0-773e-42df-b2af-...
```

## User has Microsoft Calling Plan or is enabled for Direct Routing

**If the user has Microsoft Calling Plan**, make sure that the **CapabilityStatus attribute is set to Enabled**, and that the **Capability is set to MCOPSTN**. You might see MCOPSTN1, MCOPSTN2, and so on. All are acceptable--as long as the Capability starts with MCOPSTN.

To check the attributes, use the following command:

```PowerShell
(Get-CsOnlineUser -Identity $user).AssignedPlan
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability** attributes:

```PowerShell
AssignedTimestamp   Capability      CapabilityStatus ServiceInstance                          ServicePlanId
-----------------   ----------      ---------------- ---------------                          -------------
07-02-2020 12:28:48 MCOEV           Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 4828c8ec-dc2e-4779-b502-...
07-02-2020 12:28:48 MCOPSTN2        Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 5a10155d-f5c1-411a-a8ec-...
07-02-2020 12:28:48 Teams           Enabled          TeamspaceAPI/NA001                       57ff2da0-773e-42df-b2af-...
```

**If the user is enabled for Direct Routing**, the user must be assigned a non-null value for OnlineVoiceRoutingPolicy. To check the attribute, use the following command:

```PowerShell
Get-CsOnlineUser -Identity $user|Select OnlineVoiceRoutingPolicy
```

The output should have a non-null value, for example:

```PowerShell
OnlineVoiceRoutingPolicy
------------------------
Test_Policy
```
 > [!NOTE]
> If your tenant is configured with a Global OnlineVoiceRoutingPolicy that applies to all users, then a user assigned policy is not required.

## User has Enterprise Voice enabled

To check if the user has Enterprise Voice enabled, use the following command:

```PowerShell
Get-CsOnlineUser -Identity $user|Select EnterpriseVoiceEnabled
```

The output should look like:

```PowerShell
EnterpriseVoiceEnabled
----------------------
                  True
```
 > [!NOTE]
> When assigning a phone number, Enterprise Voice enabled is automatically set to True. If a phone number is assigned and the value is False, you must use the [Set-CsPhoneNumber](/powershell/module/teams/set-csphonenumberassignment) cmdlet to set the value to True. 

## User is homed online and not in Skype for Business on premises

To ensure the user is homed online and not in Skype for Business on premises, the RegistrarPool must not be null and the HostingProvider must contain a value that starts with "sipfed.online." To check the values, use the following command:

```PowerShell
Get-CsOnlineUser -Identity $user|Select RegistrarPool, HostingProvider
```

The output should be similar to:

```PowerShell
RegistrarPool                 HostingProvider
-------------                 ---------------
sippoolbn10M02.infra.lync.com sipfed.online.lync.com
```

## User has Teams Calling Policy enabled

The user's effective TeamsCallingPolicy must have AllowPrivateCalling set to true. By default, users inherit the global policy, which has AllowPrivateCallingPolicy set to true by default.

To get the TeamsCallingPolicy for a user and to check that AllowPrivateCalling is set to true, use the following command:

```PowerShell
if (($p=Get-CsUserPolicyAssignment -Identity $user -PolicyType TeamsCallingPolicy) -eq $null) {Get-CsTeamsCallingPolicy -Identity Global} else {Get-CsTeamsCallingPolicy -Identity $p.PolicyName}
```

The output should look like:

```PowerShell
Identity                   : Global
Description                :
AllowPrivateCalling        : True
AllowWebPSTNCalling        : True
AllowVoicemail             : UserOverride
AllowCallGroups            : True
AllowDelegation            : True
AllowCallForwardingToUser  : True
AllowCallForwardingToPhone : True
PreventTollBypass          : False
BusyOnBusyEnabledType      : Disabled
MusicOnHoldEnabledType     : Enabled
```

## Additional notes

- You might need to restart the Teams client after making any of these configuration changes.

- If you recently updated any of the above criteria, you might need to wait a few hours for the client to receive the new settings.

- If you still don't see the dial pad, check if there's a provisioning error by using the following command:

  ```PowerShell
  Get-CsOnlineUser -Identity $user|Select UserValidationErrors
  ```

- If it's been more than 24 hours and you're still seeing problems, contact Support.

## Related articles

- [Microsoft Teams add-on licensing](/MicrosoftTeams/teams-add-on-licensing/assign-teams-add-on-licenses)
- [Get-CsOnlineUser](/powershell/module/teams/get-csonlineuser)
- [Get-CsUserPolicyAssignment](/powershell/module/teams/get-csuserpolicyassignment)
- [Plan for Shared Calling](shared-calling-plan.md)
- [PSTN connectivity options](pstn-connectivity.md)
- [Plan your Teams voice solution](cloud-voice-landing-page.md)
