---
title: "Get-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37a1cbc9-b8b2-423c-8ebb-7947fdcad24e
description: "Retrieves the routing configuration object, which contains a list of all voice routes defined within a Skype for Business Server 2015 deployment. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsRoutingConfiguration
 
Retrieves the routing configuration object, which contains a list of all voice routes defined within a Skype for Business Server 2015 deployment. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example retrieves the routing configuration. To retrieve individual voice routes, use the **Get-CsVoiceRoute** cmdlet.
  
```
Get-CsRoutingConfiguration
```

## Detailed Description

Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet is used to retrieve the global instance that holds a list of all voice routes defined within the Skype for Business Server 2015 deployment. To retrieve individual voice routes or to retrieve them as individual objects rather than as a list, use the **Get-CsVoiceRoute** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |There can be only one instance of this object, so this parameter does nothing.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration to retrieve. The only possible value is Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the routing configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsRoutingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.Writable.Policy.Voice.PSTNRoutingSettings object.
  
## See also

#### 

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

