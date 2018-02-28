---
title: "New-CsThirdPartyVideoSystemPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab6f880f-9b9f-45dd-b729-de9a837324ef
description: "Creates a new third-party video system policy for use with video teleconferencing (VTC) devices. These policies determine whether or not the VTC is allowed to send low-resolution video."
---

# New-CsThirdPartyVideoSystemPolicy
[]
Creates a new third-party video system policy for use with video teleconferencing (VTC) devices. These policies determine whether or not the VTC is allowed to send low-resolution video.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
New-CsThirdPartyVideoSystemPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SupportsSendingLowResolution <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new third-party video system policy assigned to the Redmond site. With this policy, VTCs will not be allowed to send low resolution video; that's because the SupportsSendingLowResolution parameter has been set to False ($False). 
  
```
New-CsThirdPartyVideoSystemPolicy -Identity "site:Redmond" -SupportsSendingLowResolution $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices.
  
One key management task related to VTC devices is to enable (or disable) the ability of these devices to send low-resolution video. By default, VTC devices are allowed to send low-resolution video. However, administrators can create third-party video system policies that disable the use of low-resolution video. This might be useful for devices located in conference rooms or other areas where low-resolution video is not considered acceptable. The New-CsThirdPartyVideoSystem cmdlet provides a way for administrators to create these third-party video system policies.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the unique Identity to be assigned to the policy. Third party video system policies can be created at the site or per-user scope. To create a policy at the site scope, use syntax similar to this: -Identity "site:Redmond". To create a policy at the per-user scope, use syntax similar to this: -Identity "RedmondVideoSystemPolicy".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _SupportsSendingLowResolution_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not low-resolution video can be sent by a VTC device. The default value is True ($True).  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the third-party video system policy being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The New-CsThirdPartyVideoSystemPolicy cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The New-CsThirdPartyVideoSystemPolicy cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ThirdPartyVideoSystem.ThirdPartyVideoSystemPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsThirdPartyVideoSystemPolicy](get-csthirdpartyvideosystempolicy.md)
  
[Grant-CsThirdPartyVideoSystemPolicy](grant-csthirdpartyvideosystempolicy.md)
  
[Remove-CsThirdPartyVideoSystemPolicy](remove-csthirdpartyvideosystempolicy.md)
  
[Set-CsThirdPartyVideoSystemPolicy](set-csthirdpartyvideosystempolicy.md)

