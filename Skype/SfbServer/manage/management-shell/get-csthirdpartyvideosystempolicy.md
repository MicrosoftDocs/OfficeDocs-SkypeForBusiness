---
title: "Get-CsThirdPartyVideoSystemPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f6f539bc-de45-4285-bd51-8fa22cf22518
description: "Returns information about the third-party video system policies configured for use in the organization. These policies determine whether or not a VTC (video teleconferencing) device is allowed to send low-resolution video."
---

# Get-CsThirdPartyVideoSystemPolicy
 
Returns information about the third-party video system policies configured for use in the organization. These policies determine whether or not a VTC (video teleconferencing) device is allowed to send low-resolution video.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Get-CsThirdPartyVideoSystemPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the third-party video system policies currently configured for use in the organization.
  
```
Get-CsThirdPartyVideoSystemPolicy
```

### Example 2

In Example 2, information for a single third-party video system policy is returned: the per-user policy with the Identity RedmondVideoSystemPolicy.
  
```
Get-CsThirdPartyVideoSystemPolicy -Identity "RedmondVideoSystemPolicy"
```

### Example 2

Example 3 returns information about all the third-party video system policies that have been configured at the site scope. To do this, the Filter parameter is included, along with the filter value "site:\*".
  
```
Get-CsThirdPartyVideoSystemPolicy -Filter "site:*"
```

### Example 4

The command shown in Example 4 returns information for all the third-party video system policies that allow users to send low-resolution video. To carry out this task, Get-CsThirdPartyVideoSystemPolicy is first used to return a collection of all the policies configured for use in the organization. That collection is then pipe to the Where-Object cmdlet, which picks out only those policies where the SupportsSendingLowResolution property is set to True ($True).
  
```
Get-CsThirdPartVideoSystemPolicy | Where-Object {$_.SupportsSendingLowResolution -eq $True}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices.
  
One key management task related to VTC devices is to enable (or disable) the ability of these devices to send low-resolution video. By default, VTC devices are allowed to send low-resolution video. However, administrators can create third-party video system policies that disable the use of low-resolution video. This might be useful for devices located in conference rooms or other areas where low-resolution video is not considered acceptable. The Get-CsThirdPartyVideoSystem cmdlet provides a way for administrators to return information about the third-party video system policies configured for use in the organization.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to do a wildcard search for third-party video system policies. For example, to find all the policies configured at the site scope, use this syntax:  <br/>  `-Filter "site:*"` <br/> To find all the per-user policies, use this syntax:  <br/>  `-Filter "tag:*"` <br/> Note that you can only filter on the Identity property.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the policy when it was created. Third-party video system policies can be assigned at the global, site, or per-user scope. To refer to the global instance, use this syntax:  <br/>  `-Identity "global"` <br/> To refer to a policy at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To refer to a policy at the per-user scope, use syntax similar to the following:  <br/>  `-Identity "RedmondVideoSystemPolicy"` <br/> Wildcard characters such as the asterisk (\*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead. If neither the Identity nor the Filter parameter is specified the Get-CsThirdPartyVideoSystemPolicy cmdlet returns information about all the video system policies configured for use in your organization.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the third-party video system policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the third-party video system policies are being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Get-CsThirdPartyVideoSystemPolicy cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The Get-CsThirdPartyVideoSystemPolicy cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ThirdPartyVideoSystem.ThirdPartyVideoSystemPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Grant-CsThirdPartyVideoSystemPolicy](grant-csthirdpartyvideosystempolicy.md)
  
[New-CsThirdPartyVideoSystemPolicy](new-csthirdpartyvideosystempolicy.md)
  
[Remove-CsThirdPartyVideoSystem](remove-csthirdpartyvideosystem.md)
  
[Set-CsThirdPartyVideoSystemPolicy](set-csthirdpartyvideosystempolicy.md)

