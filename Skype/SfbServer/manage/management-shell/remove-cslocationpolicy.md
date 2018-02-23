---
title: "Remove-CsLocationPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8fb98533-6474-4071-a74c-ce3f6fa2d326
description: "Removes the specified location policy. (Location policies are used with the Enhanced 9-1-1 service to enable those who answer 911 calls to determine the caller's geographic location based on the phone number of the telephone or device used to make the call.) This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsLocationPolicy
[]
Removes the specified location policy. (Location policies are used with the Enhanced 9-1-1 service to enable those who answer 911 calls to determine the caller's geographic location based on the phone number of the telephone or device used to make the call.) This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLocationPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 uses the **Remove-CsLocationPolicy** cmdlet to delete the location policy with the Identity Reno. When a per-user policy is removed, users or groups who were assigned that policy will automatically use the policy configured for their site instead. If no policy has been configured for their site, then these users and groups will use the global location policy.
  
```
Remove-CsLocationPolicy -Identity Reno
```

### EXAMPLE 2

Example 2 deletes all the location policies where the EnhancedEmergencyServicesEnabled property is False. (In other words, it deletes all location policies that don't enable E9-1-1.) To do this, the command first uses the **Get-CsLocationPolicy** cmdlet to retrieve all the location policies currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the retrieved data to those policies where the EnhancedEmergencyServicesEnabled property is equal to (-eq) False ($False). Finally, this filtered collection is passed to the **Remove-CsLocationPolicy** cmdlet, which proceeds to delete each policy in the collection.
  
```
Get-CsLocationPolicy | Where-Object {$_.EnhancedEmergencyServicesEnabled -eq $false} | Remove-CsLocationPolicy
```

## Detailed Description

The location policy is used to apply settings that relate to E9-1-1 functionality. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. This cmdlet removes an existing location policy.
  
In addition to removing site and per-user location policies, this cmdlet can also be used to remove the global location policy. In that case, however, the policy will not actually be removed; instead, the policy settings will simply be reset to their default values.
  
If this cmdlet is run against a per-user location policy that is assigned to user, you will be prompted to confirm the deletion.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the location policy you want to remove. To remove the global location policy (which simply resets that policy to its default values), use a value of Global. For a policy created at the site scope, this value will be in the form site:\<site name\>, where site name is the name of a site defined in the Skype for Business Server 2015 deployment (for example, site:Redmond). For a policy created at the per-user scope, this value will simply be the name of the policy, such as Bldg30Floor3Sector1.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifying this parameter will bypass any confirmation prompts and the deletion will occur without any warning notice. For example, if a per-user location policy is assigned to one or more users, a confirmation prompt will be displayed before deletion if this parameter is not included in the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the location policy is being removed. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object. Accepts pipelined input of location policy objects.
  
## Return Types

This cmdlet does not return a value or object. Instead, the cmdlet removes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object.
  
## See also

#### 

[New-CsLocationPolicy](new-cslocationpolicy.md)
  
[Set-CsLocationPolicy](set-cslocationpolicy.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)
  
[Test-CsLocationPolicy](test-cslocationpolicy.md)

