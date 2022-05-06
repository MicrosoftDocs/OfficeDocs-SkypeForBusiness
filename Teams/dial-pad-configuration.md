---
title: Teams dial pad configuration
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: "Learn about how to configure the dial pad in the Teams client so that users can access Public Switched Telephone Network (PSTN) functionality."
---

# Dial pad configuration

In the Teams client, the dial pad enables users to access Public Switched Telephone Network (PSTN) functionality. The dial pad is available for users with a Phone System license, provided they are configured properly. The following criteria are all required for the dial pad to show:

- User has an enabled Phone System (“MCOEV”) license
- User has Microsoft Calling Plan, Operator Connect or is enabled for Direct Routing
- User has Enterprise Voice enabled
- User is homed online and not in Skype for Business on premises
- User has Teams Calling Policy enabled

The following sections describe how to use PowerShell to check the criteria. In most cases, you need to look at various properties in the output of the Get-CsOnlineUser cmdlet. Examples assume $user is either the UPN or sip address of the user.

## User has an enabled Phone System (“MCOEV”) license

You must ensure that the assigned plan for the user shows the **CapabilityStatus attribute set to Enabled** and the **Capability set to MCOEV** (Phone System license). You might see MCOEV, MCOEV1, and so on. All are acceptable--as long as the Capability starts with MCOEV.

To check that the attributes are set correctly, use the following command:

```
(Get-CsOnlineUser -Identity $user).AssignedPlan
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability** attributes:

```
AssignedTimestamp   Capability      CapabilityStatus ServiceInstance                          ServicePlanId
-----------------   ----------      ---------------- ---------------                          -------------
07-02-2020 12:28:48 MCOEV           Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 4828c8ec-dc2e-4779-b502-…
07-02-2020 12:28:48 Teams           Enabled          TeamspaceAPI/NA001                       57ff2da0-773e-42df-b2af-…
```


## User has Microsoft Calling Plan, Operator Connect OR is enabled for Direct Routing

**If the user has Microsoft Calling Plan**, you must ensure that the **CapabilityStatus attribute is set to Enabled**, and that the **Capability is set to MCOPSTN**. You might see MCOPSTN1, MCOPSTN2, and so on. All are acceptable--as long as the Capability starts with MCOPSTN.

To check the attributes, use the following command:

```
(Get-CsOnlineUser -Identity $user).AssignedPlan
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability** attributes:

```  
AssignedTimestamp   Capability      CapabilityStatus ServiceInstance                          ServicePlanId
-----------------   ----------      ---------------- ---------------                          -------------
07-02-2020 12:28:48 MCOEV           Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 4828c8ec-dc2e-4779-b502-…
07-02-2020 12:28:48 MCOPSTN2        Enabled          MicrosoftCommunicationsOnline/NOAM-4A-S7 5a10155d-f5c1-411a-a8ec-…
07-02-2020 12:28:48 Teams           Enabled          TeamspaceAPI/NA001                       57ff2da0-773e-42df-b2af-…
```
**If the user is enabled for Operator Connect**, the user must have a non-null value for TeamsCarrierEmergencyCallRoutingPolicy. To check the attribute, use the following command:
  
```
Get-CsOnlineUser -Identity $user|Select TeamsCarrierEmergencyCallRoutingPolicy
```

The output should have a non-null value, for example:

```
TeamsCarrierEmergencyCallRoutingPolicy
--------------------------------------
Synergy_98d1a5cb-d3e6-4306-885e-69a95f2da5c3
```

**If the user is enabled for Direct Routing**, the user must be assigned a non-null value for OnlineVoiceRoutingPolicy. To check the attribute, use the following command:
  
```
Get-CsOnlineUser -Identity $user|Select OnlineVoiceRoutingPolicy 
```

The output should have a non-null value, for example:

```
OnlineVoiceRoutingPolicy
------------------------
Test_Policy
```

## User has Enterprise Voice enabled

To check if the user has Enterprise Voice enabled, use the following command:

```
Get-CsOnlineUser -Identity $user|Select EnterpriseVoiceEnabled
```

The output should look like:

```
EnterpriseVoiceEnabled
----------------------
                  True

```
 
## User is homed online and not in Skype for Business on premises

To ensure the user is homed online and not in Skype for Business on premises, the RegistrarPool must not be null and the HostingProvider must contain a value that starts with “sipfed.online.”  To check the values, use the following command:

```
Get-CsOnlineUser -Identity $user|Select RegistrarPool, HostingProvider
```

The output should be similar to:

```
RegistrarPool                 HostingProvider
-------------                 ---------------
sippoolbn10M02.infra.lync.com sipfed.online.lync.com
```

## User has Teams Calling Policy enabled

The user’s effective TeamsCallingPolicy must have AllowPrivateCalling set to true.  By default, users inherit the global policy, which has AllowPrivateCallingPolicy set to true by default.

To get the TeamsCallingPolicy for a user and to check that AllowPrivateCalling is set to true, use the following command:

```
if (($p=Get-CsUserPolicyAssignment -Identity $user -PolicyType TeamsCallingPolicy) -eq $null) {Get-CsTeamsCallingPolicy -Identity Global} else {Get-CsTeamsCallingPolicy -Identity $p.PolicyName}
```

The output should look like:

```
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

-	You may need to restart the Teams client after making any of these configuration changes.

-	If you recently updated any of the above criteria, you may need to wait a few hours for the client to receive the new settings.

-	If you still don’t see the dial pad, check if there is a provisioning error by using the following command:

  ```
  Get-CsOnlineUser -Identity $user|Select UserValidationErrors
  ```

-	 If it has been more than 24 hours and you are still seeing problems, contact Support.


