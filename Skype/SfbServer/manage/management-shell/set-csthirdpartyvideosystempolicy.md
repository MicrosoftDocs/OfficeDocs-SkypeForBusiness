---
title: "Set-CsThirdPartyVideoSystemPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5022535e-fcdd-4fac-ab12-d1ac43267d0a
description: "Creates a new third-party video system policy for use with video teleconferencing (VTC) devices. These policies determine whether or not the VTC is allowed to send low-resolution video."
---

# Set-CsThirdPartyVideoSystemPolicy
 
Creates a new third-party video system policy for use with video teleconferencing (VTC) devices. These policies determine whether or not the VTC is allowed to send low-resolution video.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsThirdPartyVideoSystemPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 modifies the per-user third-party video system policy RedmondVideoSystemPolicy. In this example, the ability to send low-resolution video is disabled.
  
```
Set-CsThirdPartyVideoSystemPolicy -Identity "RedmondVideoSystemPolicy" -SupportsSendingLowResolution $False
```

### Example 2

In Example 2, the ability to send low-resolution video is disabled for all third-party video system policies configured at the site scope. To do that, the command first calls Get-CsThirdPartyVideoSystemPolicy along with the Filter parameter; the filter value "site:\*" limits returned data to policies configured at the site scope. That collection of site-based policies is then piped to the Set-CsThirdPartyVideoSystemPolicy to set the SupportsSendingLowResolution property to False ($False).
  
```
Get-CsThirdPartyVideoSystemPolicy -Filter "site:*" | Set-CsThirdPartyVideoSystemPolicy -SupportsSendingLowResolution $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices.
  
One key management task related to VTC devices is to enable (or disable) the ability of these devices to send low-resolution video. By default, VTC devices are allowed to send low-resolution video. However, administrators can create third-party video system policies that disable the use of low-resolution video. This might be useful for devices located in conference rooms or other areas where low-resolution video is not considered acceptable. The New-CsThirdPartyVideoSystem cmdlet provides a way for administrators to create these third-party video system policies. Both the global policy and any custom policies you create can later be modified by using the Set-CsThirdPartyVideoSystemPolicy cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the policy when it was created. Third-party video system policies can be created at the global, site, or per-user scope. To refer to the global instance, use this syntax:  <br/>  `-Identity "global"` <br/> To refer to a policy at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To refer to a policy at the per-user scope, use syntax similar to the following:  <br/>  `-Identity "RedmondVideoSystemPolicy"` <br/> Wildcard characters such as the asterisk (\*) cannot be used with the Identity parameter. If this parameter is not specified then Set-CsThirdPartyVideoSystemPolicy will modify the global video system policy.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _SupportsSendingLowResolution_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not low-resolution video can be used in conjunction with a VTC device. The default value is True ($True).  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the third-party video system policy being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsThirdPartyVideoSystemPolicy cmdlet accepts pipelined instance of the Microsoft.Rtc.Management.WritableConfig.Policy.ThirdPartyVideoSystem.ThirdPartyVideoSystemPolicy object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Set-CsThirdPartyVideoSystemPolicy cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ThirdPartyVideoSystem.ThirdPartyVideoSystemPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsThirdPartyVideoSystemPolicy](get-csthirdpartyvideosystempolicy.md)
  
[Grant-CsThirdPartyVideoSystemPolicy](grant-csthirdpartyvideosystempolicy.md)
  
[New-CsThirdPartyVideoSystemPolicy](new-csthirdpartyvideosystempolicy.md)
  
[Remove-CsThirdPartyVideoSystemPolicy](remove-csthirdpartyvideosystempolicy.md)

