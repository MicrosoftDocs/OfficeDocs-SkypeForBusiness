---
title: "Remove-CsLocationPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8fb98533-6474-4071-a74c-ce3f6fa2d326
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsLocationPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified location policy. (Location policies are used with the Enhanced 9-1-1 service to enable those who answer 911 calls to determine the caller's geographic location based on the phone number of the telephone or device used to make the call.) This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLocationPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

The location policy is used to apply settings that relate to E9-1-1 functionality. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. This cmdlet removes an existing location policy.
  
In addition to removing site and per-user location policies, this cmdlet can also be used to remove the global location policy. In that case, however, the policy will not actually be removed; instead, the policy settings will simply be reset to their default values.
  
If this cmdlet is run against a per-user location policy that is assigned to user, you will be prompted to confirm the deletion.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLocationPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsLocationPolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the location policy you want to remove. To remove the global location policy (which simply resets that policy to its default values), use a value of Global. For a policy created at the site scope, this value will be in the form site:\<site name\>, where site name is the name of a site defined in the Lync Server deployment (for example, site:Redmond). For a policy created at the per-user scope, this value will simply be the name of the policy, such as Bldg30Floor3Sector1.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifying this parameter will bypass any confirmation prompts and the deletion will occur without any warning notice. For example, if a per-user location policy is assigned to one or more users, a confirmation prompt will be displayed before deletion if this parameter is not included in the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object. Accepts pipelined input of location policy objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value or object. Instead, the cmdlet removes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsLocationPolicy](new-cslocationpolicy.md)
  
[Set-CsLocationPolicy](set-cslocationpolicy.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)
  
[Test-CsLocationPolicy](test-cslocationpolicy.md)

