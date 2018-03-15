---
title: "Remove-CsPinPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 60bebb77-4181-4c5c-9c0e-dd1ece71f1d2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsPinPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified personal identification number (PIN) policy. PIN authentication and PIN policies enable users to access Lync Server by providing a PIN instead of a user name and password. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsPinPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the per-user PIN policy with the Identity RedmondUsersPinPolicy.
  
```
Remove-CsPinPolicy -Identity RedmondUsersPinPolicy
```

### EXAMPLE 2

The command shown in Example 2 removes all the PIN policies that have been configured at the site scope. To do this, the **Get-CsPinPolicy** cmdlet is used, along with the Filter parameter, to return a collection of all the policies that have an Identity that begins with the characters "site:". This collection is then piped to the **Remove-CsPinPolicy** cmdlet, which deletes each policy in the collection. 
  
```
Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy
```

### EXAMPLE 3

In Example 3, the **Get-CsPinPolicy** cmdlet, the **Where-Object** cmdlet, and the **Remove-CsPinPolicy** cmdlet are used to delete all the PIN policies where the AllowCommonPatterns property is True. To do this, the **Get-CsPinPolicy** cmdlet is first used to return a collection of all the PIN policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those policies where AllowCommonPatterns is equal to True. Finally, that filtered collection is piped to the **Remove-CsPinPolicy** cmdlet, which deletes each policy in the collection. 
  
```
Get-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy
```

### EXAMPLE 4

The command shown in Example 4 deletes all the PIN policies configured at the per-user and site scopes; this is done by using the **Get-CsPinPolicy** cmdlet to return a collection of all the PIN policies configured for use in the organization, and then piping that entire collection to the **Remove-CsPinPolicy** cmdlet. Note that the global policy will also be included in this collection. However, the global policy will not be deleted. Instead, all the properties in the global policy will be reset to their default values. 
  
```
Get-CsPinPolicy | Remove-CsPinPolicy
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server enables users to connect to the system or to join public switched telephone network (PSTN) conferences via telephone. Typically, logging on to the system or joining a conference requires the user to enter a user name or password; unfortunately, entering a user name and password can be a problem if you are using a phone that does not have an alphanumeric keypad. Because of that, Lync Server enables you to supply users with numeric-only PINs; when prompted, users can then log on to the system or join a conference by entering the PIN instead of a user name and password.
  
Lync Server uses PIN policies to manage PIN authentication properties; for example, you can specify the minimum length for a PIN and also determine whether you will allow PINs that use "common patterns" such as consecutive digits (for example, a PIN like 123456). In addition to the global PIN policy created for you when you install Lync Server you can create custom PIN policies applied to the site or the per-user scope.
  
The **Remove-CsPinPolicy** cmdlet enables you to remove PIN policies that have been configured at either the site scope or the per-user scope. When you remove a site-scoped policy or a per-user policy, those policies will be deleted and no longer be available for use. In addition, any users who were assigned those policies will automatically inherit the next policy in the policy hierarchy (global, site, service, per-user). For example, if you remove a site policy then all the users who were previously affected by that policy will have their PIN settings managed by the global policy. 
  
You can also run the **Remove-CsPinPolicy** cmdlet against the global policy. In that case, however, the policy will not be removed: that's because you cannot delete the global policy. Instead, all the properties of the global policy will be reset to their default values. For example, suppose you have configured the global policy to use a minimum PIN length of 11 digits. If you remove the global policy, the minimum PIN length will be reset to the default length of 5 digits. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsPinPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsPinPolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier assigned to the policy when it was created. PIN policies can be assigned at the global, site, or per-user scope. To refer to the global instance, use this syntax: -Identity global. To refer to a policy at the site scope, use this syntax: -Identity site:Redmond. To refer to a policy at the per-user scope, use syntax similar to this: -Identity RedmondPINPolicy.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy object. The **Remove-CsPinPolicy** cmdlet accepts pipelined input of the PIN policy object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Remove-CsPinPolicy** cmdlet does not return a value or object. Instead, the cmdlet removes one or more instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsPinPolicy](get-cspinpolicy.md)
  
[Grant-CsPinPolicy](grant-cspinpolicy.md)
  
[New-CsPinPolicy](new-cspinpolicy.md)
  
[Set-CsPinPolicy](set-cspinpolicy.md)

