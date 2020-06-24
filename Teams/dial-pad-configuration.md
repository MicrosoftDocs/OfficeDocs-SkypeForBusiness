---
title: Teams dial pad configuration
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.assetid: 589bf5f5-490a-4215-8588-99bab7d33e31
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
- CSH
description: "Learn about how to configure the dial pad in the Teams client so that users can access PSTN functionality."
---

# Overview

In the Teams client, the dial pad enables users to access Public Switched Telephone Network (PSTN) functionality. The dial pad is available for users with a Phone System license, provided they are configured properly. The following sections describe the criteria required for the dial pad to show. All of the criteria must be satisfied for the dialpad to show.

## User has an enabled Phone System (“MCOEV”) license

Use the following PowerShell cmdlet to ensure that CapabilityStatus is Enabled and Capability Plan = MCOEV:

```
Get-CsOnlineUser -Identity $user|select AssignedPlan|fl
```



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

- If the user has Microsoft Calling Plan, 

  ```
  Get-CsOnlineUser -Identity $user|select AssignedPlan|fl
  ``` 

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

- If the user is enabled for Direct Routing:
  
  ```
  Get-CsOnlineUser -Identity $user|Select OnlineVoiceRoutingPolicy
  ```

  ```
  OnlineVoiceRoutingPolicy
  ------------------------
  Test_Policy
  ```

## User has Enterprise Voice enabled

```
Get-CsOnlineUser -Identity $user|Select EnterpriseVoiceEnabled
```

```
EnterpriseVoiceEnabled
----------------------
                  True

```


 
## User is homed online and not in Skype for Business on premises

```
Get-CsOnlineUser -Identity $user|Select RegistrarPool, HostingProvider
```

```
RegistrarPool                 HostingProvider
-------------                 ---------------
sippoolbn10M02.infra.lync.com sipfed.online.lync.com
```

## User has Teams Calling Policy enabled

The user’s effective TeamsCallingPolicy must have AllowPrivateCalling=true. By default, users are not assigned an instance of TeamsCallingPolicy, in which case they inherit the global policy, which by default has AllowPrivateCallingPolicy=true.

You can use the following cmdlet to get the effective instance of TeamsCallingPolicy for a user. Then check that AllowPrivateCalling=true as shown in yellow below.

```
if (($p=(get-csonlineuser -Identity $user).TeamsCallingPolicy) -eq $null) {Get-CsTeamsCallingPolicy -Identity global} else {get-csteamscallingpolicy -Identity $p}
```

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

## User has a phone number assigned


```
Get-CsOnlineUser -Identity $user|Select LineUri
```

## Additional notes

-	You may need to restart the Teams client after making any of these configuration changes.
-	If you recently updated any of the above criteria, you may need to wait a few hours for the client to receive the new settings.
-	If you still don’t see the Dial pad, check if there is a provisioning error:
Get-CsOnlineUser -Identity $user|Select McoValidationError
-	 If it has been more than 24 hours, contact Support.







  

  


    
## Related topics

- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies ](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
