---
title: "Set-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab69c6e8-262a-4ecb-b1af-513383c494fe
description: "Modifies a list of voice routes. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsRoutingConfiguration
 
Modifies a list of voice routes. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

It takes several steps to modify a voice route within a routing configuration. In this example, we start by retrieving the routing configuration object by calling the **Get-CsRoutingConfiguration** cmdlet. We assign the object retrieved (there will be only one) to the variable $a.
  
In line 2 of this example we retrieve the contents of the Route property from variable $a, which is a collection of voice route objects. We then pipe that collection to the **Where-Object** cmdlet, where we search the collection for all voice route objects with a Name matching the string LocalRoute. We assign that object to the variable $b.
  
Next, we modify the LocalRoute voice route object by assigning the value $False to the property SuppressCallerId. By updating that object we've updated the object in variable $a. However, that object is still only in memory. As a final step, we need to save those changes by passing $a to the Instance parameter of the **Set-CsRoutingConfiguration** cmdlet.
  
This is not the recommended way of modifying a routing configuration. To modify a routing configuration, simply change the individual voice routes with the **Set-CsVoiceRoute** cmdlet, as shown here:
  
```
Set-CsVoiceRoute -Identity LocalRoute -SuppressCallerId $False

```

That one line will accomplish the same task shown in Example 1.
  
```
$a = Get-CsRoutingConfiguration
$b = $a.Route | Where-Object {$_.Name -match "LocalRoute"}
$b.SuppressCallerId = $False
Set-CsRoutingConfiguration -Instance $a
```

## Detailed Description

Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). With this cmdlet you can modify the settings of any voice route defined within a Skype for Business Server 2015 deployment.
  
The use of this cmdlet is not recommended. To modify routing configurations, modify the individual voice routes by calling the **Set-CsVoiceRoute** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CallViaWorkCallerId_ <br/> |Optional  <br/> |System.String  <br/> |The number the system will display for the callback portion of an external call. External calls first connect the user making the call by calling a specified number (typically the user's desk phone), once connected to the user, the system dials the outside number. The  _CallViaWorkCallerId_ parameter specifies the number that will be displayed during the first leg, or callback segment, of the call via work external call. For more information, see [New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableLocationBasedRouting_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration. This must be Global.  <br/> |
| _Instance_ <br/> |Optional  <br/> |PstnRoutingSettings  <br/> |A routing configuration (Microsoft.Rtc.Management.WritablConfig.Policy.Voice.PstnRoutingSettings) object. An object of this type can be retrieved by calling the **Get-CsRoutingConfiguration** cmdlet. <br/> |
| _Route_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of all voice routes (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route objects) defined for the Skype for Business Server 2015 deployment.  <br/> You should modify individual voice route objects by using the **Set-CsVoiceRoute** cmdlet. That is the recommended way of modifying routes in this list. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.WritableConfig.Management.Policy.Voice.PSTNRoutingSettings object. Accepts pipelined input of a routing configuration object.
  
## Return Types

The **Set-CsRoutingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings object.
  
## See also

#### 

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
  
[Set-CsVoiceRoute](set-csvoiceroute.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)
  
[New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)

