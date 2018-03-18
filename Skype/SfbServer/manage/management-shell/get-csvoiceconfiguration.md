---
title: "Get-CsVoiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c5e7afa3-28d3-4bf9-a2f2-c34932c9a3cd
description: "Retrieves the voice configuration object, which contains a full list of all voice test configurations defined for the Skype for Business Server 2015 deployment. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsVoiceConfiguration
 
Retrieves the voice configuration object, which contains a full list of all voice test configurations defined for the Skype for Business Server 2015 deployment. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example retrieves the voice configuration. To retrieve the voice test configurations, use the **Get-CsVoiceTestConfiguration** cmdlet.
  
```
Get-CsVoiceConfiguration
```

## Detailed Description

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet is used to retrieve the global instance that holds a list of all voice test configurations defined within the Skype for Business Server 2015 deployment. To retrieve individual voice test configurations or to retrieve them as individual objects rather than as a list, use the **Get-CsVoiceTestConfiguration** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |There can only be one instance of this object, so this parameter does nothing.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the voice configuration to retrieve. The only possible value is Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object.
  
## See also

#### 

[Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)
  
[Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

