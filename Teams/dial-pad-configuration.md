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
localization_priority: Normal
f1.keywords:
- NOCSH
description: "Learn about how to configure the dial pad in the Teams client so that users can access Public Switched Telephone Network (PSTN) functionality."
---

# Dial pad configuration

In the Teams client, the dial pad enables users to access Public Switched Telephone Network (PSTN) functionality. The dial pad is available for users with a Phone System license, provided they are configured properly. The following criteria are all required for the dial pad to show:

- User has an enabled Phone System (“MCOEV”) license
- User has Microsoft Calling Plan or is enabled for Direct Routing
- User has Enterprise Voice enabled
- User is homed online and not in Skype for Business on premises
- User has Teams Calling Policy enabled

The following sections describe how to use PowerShell to check the criteria. In most cases, you need to look at various properties in the output of the Get-CsOnlineUser cmdlet. Examples assume $user is either the UPN or sip address of the user.

## User has an enabled Phone System (“MCOEV”) license

You must ensure that the assigned plan for the user shows the **CapabilityStatus attribute set to Enabled** and the **Capability Plan set to MCOEV** (Phone System license). You might see MCOEV, MCOEV1, and so on. All are acceptable--as long as the Capability Plan starts with MCOEV.

To check that the attributes are set correctly, use the following command:

```
Get-CsOnlineUser -Identity $user|select AssignedPlan|fl
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability Plan** attributes:

```
<Plan SubscribedPlanId="2f9eda01-4630-4a5c-bdb3-cf195f22d240"  
   ServiceInstance="MicrosoftCommunicationsOnline/NOAM-0M-DMT" 
   CapabilityStatus="Enabled"  
   AssignedTimestamp="2020-04-21T18:31:13Z" 
   ServicePlanId="4828c8ec-dc2e-4779-b502-87ac9ce28ab7" 
   xmlns="http://schemas.microsoft.com/online/directoryservices/change/2008/11"> 
  <Capability> 
     <Capability Plan="MCOEV" 
     xmlns="http://schemas.microsoft.com/online/MCO/2009/01"/> 
  </Capability>
</Plan>
```


## User has Microsoft Calling Plan OR is enabled for Direct Routing

**If the user has Microsoft Calling Plan**, you must ensure that the **CapabilityStatus attribute is set to Enabled**, and that the **Capability Plan is set to MCOPSTN**. You might see MCOPSTN1, MCOPSTN2, and so on. All are acceptable--as long as the Capability Plan starts with MCOPSTN.

To check the attributes, use the following command:

```
Get-CsOnlineUser -Identity $user|select AssignedPlan|fl
```

The output will look like the following. You only need to check the **CapabilityStatus** and the **Capability Plan** attributes:

```  
<Plan SubscribedPlanId="71d1258e-a4e6-443f-884e-0f3d6f644bb1" 
ServiceInstance="MicrosoftCommunicationsOnline/NOAM-0M-DMT" 
CapabilityStatus="Enabled"    
AssignedTimestamp="2018-09-18T18:41:42Z" 
ServicePlanId="5a10155d-f5c1-411a-a8ec-e99aae125390" 
xmlns="http://schemas.microsoft.com/online/directoryservices/change/2008/11">
 <Capability>
    <Capability Plan="MCOPSTN2" 
    xmlns="http://schemas.microsoft.com/online/MCO/2009/01" />
 </Capability>
</Plan>
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
if (($p=(get-csonlineuser -Identity $user).TeamsCallingPolicy) -eq $null) {Get-CsTeamsCallingPolicy -Identity global} else {get-csteamscallingpolicy -Identity $p}
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
  Get-CsOnlineUser -Identity $user|Select McoValidationError
  ```

-	 If it has been more than 24 hours and you are still seeing problems, contact Support.


