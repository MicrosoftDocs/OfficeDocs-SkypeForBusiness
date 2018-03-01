---
title: "Get-CsLocationPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d338af1b-3865-4010-a7fc-d5841c515ae6
description: "Returns information about how (or if) the Enhanced 9-1-1 (E9-1-1) Location Information service has been configured. The E9-1-1 service enables those who answer emergency calls to determine the caller's geographic location. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsLocationPolicy
 
Returns information about how (or if) the Enhanced 9-1-1 (E9-1-1) Location Information service has been configured. The E9-1-1 service enables those who answer emergency calls to determine the caller's geographic location. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLocationPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns a collection of all the location policies currently in use in your organization. This is done simply by calling the **Get-CsLocationPolicy** cmdlet without any parameters.
  
```
Get-CsLocationPolicy
```

### EXAMPLE 2

The command shown in Example 2 returns only those location policies that have an Identity equal to Reno. Because identities must be unique, this command will only return, at most, one location policy.
  
```
Get-CsLocationPolicy -Identity Reno
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return all the location policies that have been configured at the per-use scope. (Policies configured at the per-user scope can be directly assigned to users and network sites.) The wildcard string tag:* tells the **Get-CsLocationPolicy** cmdlet that the returned data should be limited to those location policies that have an Identity that begins with the string value tag:. Even though you don't need to specify the tag: prefix when retrieving an individual policy, you can use that prefix to filter on all per-user policies.
  
```
Get-CsLocationPolicy -Filter tag:*
```

### EXAMPLE 4

Example 4 returns a collection of all the location policies where enhanced emergency services are disabled. To do this, the command first uses the **Get-CsLocationPolicy** cmdlet to return a collection of all the location policies currently in use in the organization. That collection is then piped to the **Where-Object** cmdlet; in turn, the **Where-Object** cmdlet applies a filter that limits the returned data to those policies where the EnhancedEmergencyServicesEnabled property is equal to (-eq) False ($False).
  
```
Get-CsLocationPolicy | Where-Object {$_.EnhancedEmergencyServicesEnabled -eq $False}
```

## Detailed Description

The location policy is used to apply settings that relate to E9-1-1 functionality. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, how the call should be routed, and so on. This cmdlet retrieves one or more location policies.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string containing wildcard characters that will retrieve location policies based on matching the Identity value of the policy to the wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the location policy you want to retrieve. To retrieve the global location policy, use a value of Global. For a policy created at the site scope, this value will be in the form site:\<site name\>, where site name is the name of a site defined in the Skype for Business Server 2015 deployment (for example, site:Redmond). For a policy created at the per-user scope, this value will simply be the name of the policy, such as Reno.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the location policy information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose location policies are being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsLocationPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object.
  
## See also

#### 

[New-CsLocationPolicy](new-cslocationpolicy.md)
  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)
  
[Set-CsLocationPolicy](set-cslocationpolicy.md)
  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)
  
[Test-CsLocationPolicy](test-cslocationpolicy.md)

