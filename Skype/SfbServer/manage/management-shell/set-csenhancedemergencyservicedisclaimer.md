---
title: "Set-CsEnhancedEmergencyServiceDisclaimer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7c7f5594-4014-4ae0-afe1-6f73340be08c
description: "Sets disclaimer text that will be used globally to prompt for location information for an Enhanced 9-1-1 (E9-1-1) implementation. This cmdlet was introduced in Lync Server 2010. It has been deprecated for use with Skype for Business Server 2015. For Skype for Business Server 2015, E9-1-1 disclaimers should be configured by using the New-CsLocationPolicy cmdlet and the Set-CsLocationPolicy cmdlet."
---

# Set-CsEnhancedEmergencyServiceDisclaimer
 
Sets disclaimer text that will be used globally to prompt for location information for an Enhanced 9-1-1 (E9-1-1) implementation. This cmdlet was introduced in Lync Server 2010. It has been deprecated for use with Skype for Business Server 2015. For Skype for Business Server 2015, E9-1-1 disclaimers should be configured by using the [New-CsLocationPolicy](new-cslocationpolicy.md) cmdlet and the [Set-CsLocationPolicy](set-cslocationpolicy.md) cmdlet.
  
```
Set-CsEnhancedEmergencyServiceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example replaces the text of the global enhanced emergency services disclaimer with the text provided in the string passed to the Body parameter. This setting can be applied only at the global scope, which is the default for Identity and therefore does not need to be specified.
  
```
Set-CsEnhancedEmergencyServiceDisclaimer -Body "Warning: If you do not provide a location, emergency services may be delayed in reaching your location should you need to call for help."
```

## Detailed Description

In order for an Enterprise Voice implementation to provide E9-1-1 service, locations must be mapped to ports, subnets, switches, and wireless access points to identify the caller's location. When the caller is connecting from outside one of these mapped points, he must enter his location manually for it to be received by emergency services. This cmdlet sets a text string that will be displayed to users who decide not to enter their location information. This message will be displayed only if the LocationRequired property of the user's location policy is set to Disclaimer. (You can retrieve location policy settings by calling the **Get-CsLocationPolicy** cmdlet.)
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Body_ <br/> |Optional  <br/> |System.String  <br/> |A string containing information that will be displayed to users who are connected from locations that cannot be resolved by the location mapping (wiremap) who choose not to enter their location manually.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This will always be Global.  <br/> |
| _Instance_ <br/> |Optional  <br/> |EnhancedEmergencyServiceDisclaimer  <br/> |A reference to an enhanced emergency service disclaimer object. Must be of type EnhancedEmergencyServiceDisclaimer.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer object. Accepts pipelined input of an enhanced emergency service disclaimer object.
  
## Return Types

This cmdlet does not return a value or an object. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer.
  
## See also

#### 

[Remove-CsEnhancedEmergencyServiceDisclaimer](remove-csenhancedemergencyservicedisclaimer.md)
  
[Get-CsEnhancedEmergencyServiceDisclaimer](get-csenhancedemergencyservicedisclaimer.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)

