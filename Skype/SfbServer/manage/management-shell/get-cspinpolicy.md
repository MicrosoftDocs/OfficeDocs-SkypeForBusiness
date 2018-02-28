---
title: "Get-CsPinPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1d627ba5-6333-466c-82a1-859deaf8d690
description: "Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Skype for Business Server 2015 by providing a PIN instead of a user name and password. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsPinPolicy
[]
Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Skype for Business Server 2015 by providing a PIN instead of a user name and password. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPinPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the PIN policies configured for use in the organization. Calling the **Get-CsPinPolicy** cmdlet without any parameters always returns the complete set of PIN policies.
  
```
Get-CsPinPolicy
```

### EXAMPLE 2

Example 2 returns a single PIN policy: the policy with the Identity site:Redmond.
  
```
Get-CsPinPolicy -Identity "site:Redmond"
```

### EXAMPLE 3

The command shown in Example 3 uses the Filter parameter to return all the policies that have been configured at the per-user scope. This is done by using the filter value "tag:*"; this value instructs the **Get-CsPinPolicy** cmdlet to return only those policies that have an Identity that begins with the characters "tag:".
  
```
Get-CsPinPolicy -Filter "tag:*"
```

### EXAMPLE 4

Example 4 returns all the PIN policies where the AllowCommonPatterns property is True. In this example, the **Get-CsPinPolicy** cmdlet is first called without any additional parameters; that returns a collection of all the PIN policies configured for use in the organization. That collection is then passed to the **Where-Object** cmdlet, which picks out only those policies where the AllowCommonPatterns property is equal to True.
  
```
Get-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True}
```

### EXAMPLE 5

Like Example 4, the command shown in Example 5 uses the **Where-Object** cmdlet to return a subset of the existing PIN policies. In this case, the **Where-Object** cmdlet retrieves only those policies where the PinLifetime property is greater than 30. That means only policies that have PIN expiration times of more than 30 days will be returned.
  
```
Get-CsPinPolicy | Where-Object {$_.PinLifetime -gt 30}
```

## Detailed Description

Skype for Business Server 2015 enables users to connect to the system, or to join public switched telephone network (PSTN) conferences via telephone. Typically, logging on to the system or joining a conference requires the user to enter a user name or password; unfortunately, entering a user name and password can be a problem if you are using a phone that does not have an alphanumeric keypad. Because of that, Skype for Business Server 2015 enables you to supply users with numeric-only PINs; when prompted, users can then log on to the system or join a conference by entering the PIN instead of a user name and password.
  
Skype for Business Server 2015 uses PIN policies to manage PIN authentication properties; for example, you can specify the minimum length for a PIN and determine whether you will allow PINs that use "common patterns" such as consecutive digits (for example, a PIN like 123456). You can use the **Get-CsPinPolicy** cmdlet to retrieve information about the PIN policies currently configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to do a wildcard search for PIN policies. For example, to find all the policies configured at the site scope, use this Filter: site:\*. To find the site policies Seattle, Seville, and Saskatoon (all of which start with the letter "S") use this Filter: site:S\*. Note that this parameter can only filter on the Identity property.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the policy when it was created. PIN policies can be assigned at the global, site, or per-user scope. To refer to the global instance, use this syntax:  <br/>  `-Identity global` <br/> To refer to a policy at the site scope, use this syntax:  <br/>  `-Identity site:Redmond` <br/> To refer to a policy at the per-user scope, use syntax similar to this:  <br/>  `-Identity RedmondPolicy` <br/> Wildcard characters such as the asterisk (\*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead.  <br/> If neither the Identity nor the Filter parameter is specified the **Get-CsPinPolicy** cmdlet returns information about all the PIN policies configured for use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the PIN policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose PIN policies are being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsPinPolicy** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsPinPolicy** cmdlet returns one or more instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPinPolicy object.
  
## See also

#### 

[Grant-CsPinPolicy](grant-cspinpolicy.md)
  
[New-CsPinPolicy](new-cspinpolicy.md)
  
[Remove-CsPinPolicy](remove-cspinpolicy.md)
  
[Set-CsPinPolicy](set-cspinpolicy.md)

