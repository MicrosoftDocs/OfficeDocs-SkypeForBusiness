---
title: "New-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ead67e35-b145-4041-ba3e-4b26c47cce1d
description: "This cmdlet returns an object containing the default settings for a routing configuration object. This cmdlet was introduced in Lync Server 2010."
---

# New-CsRoutingConfiguration
 
This cmdlet returns an object containing the default settings for a routing configuration object. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsRoutingConfiguration -Identity <XdsIdentity> [-CallViaWorkCallerId <String>] [-Confirm [<SwitchParameter>]] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This command creates an object containing the default routing configuration values and assigns that object to the variable $x. Any other use of this cmdlet will return an error.
  
```
$x = New-CsRoutingConfiguration -Identity global -InMemory
```

## Detailed Description

A routing configuration is a container for all voice routes defined within a Skype for Business Server 2015 deployment. To create a new voice route, use the **New-CsVoiceRoute** cmdlet.
  
A routing configuration can be defined only at the global level. In addition, you cannot have individually named routing configurations; there is only one voice route list for the entire Skype for Business Server 2015 deployment. In the Skype for Business Server 2015 implementation of Windows PowerShell, if you try to create an object that already exists by calling a cmdlet beginning with the New verb, you'll receive an error message. Every implementation of Skype for Business Server 2015 includes a default routing configuration object with a Global Identity. What this means is that the only voice route list that could be created already exists. So a call to the **New-CsRoutingConfiguration** cmdlet will always return an error message and will not create a new routing configuration.
  
The only exception to this is if you specify the InMemory parameter in the call to this cmdlet. This command will create an object only in memory that contains a default list of voice routes.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration. This value must be Global.  <br/> |
| _CallViaWorkCallerId_ <br/> |Optional  <br/> |System.String  <br/> |The number the system will display for the callback portion of an external call. External calls first connect the user making the call by calling a specified number (typically the user's desk phone), once connected to the user, the system dials the outside number. The  _CallViaWorkCallerId_ parameter specifies the number that will be displayed during the first leg, or callback segment, of the call via work external call. For more information, see [New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableLocationBasedRouting_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _Route_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of all voice routes (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route objects) defined for the Skype for Business Server 2015 deployment.  <br/> You can create voice route objects by using the **New-CsVoiceRoute** cmdlet. That is the recommended way of adding voice routes to this list. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Can create an in-memory object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings.
  
## See also

#### 

[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
  
[New-CsVoiceRoute](new-csvoiceroute.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

