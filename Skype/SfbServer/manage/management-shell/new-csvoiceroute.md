---
title: "New-CsVoiceRoute"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1118f74f-b06c-41d2-8b1b-5cc1e1957b77
description: "Creates a new voice route. Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet was introduced in Lync Server 2010."
---

# New-CsVoiceRoute
[]
Creates a new voice route. Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet was introduced in Lync Server 2010.
  
```
New-CsVoiceRoute -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command in this example creates a new voice route with an Identity of Route1. All other properties will be set to the default values.
  
```
New-CsVoiceRoute -Identity Route1

```

### EXAMPLE 2

The command in this example creates a new voice route with an Identity of Route1. It also adds the PSTN usage Long Distance to the list of usages and the service ID PstnGateway:redmondpool.litwareinc.com to the list of PSTN gateways.
  
```
New-CsVoiceRoute -Identity Route1 -PstnUsages @{add="Long Distance"} -PstnGatewayList @{add="PstnGateway:redmondpool.litwareinc.com"}

```

### EXAMPLE 3

This example creates a new voice route named Route1 and populates that route's list of PSTN usages with all the existing usages for the organization. The first command in this example retrieves the list of global PSTN usages. Notice that the call to the **Get-CsPstnUsage** cmdlet is in parentheses; this means that we first retrieve an object containing PSTN usage information. (Because there is only one, global, PSTN usage, only one object will be retrieved.) The command then retrieves the Usage property of this object. That property, which contains a list of usages, is assigned to the variable $x. In the second line of this example, the **New-CsVoiceRoute** cmdlet is called to create a new voice route. This voice route will have an identity of Route1. Notice the value passed to the PstnUsages parameter: @{add=$x}. This value says to add the contents of $x, which contain the phone usages list retrieved in line 1, to the list of PSTN usages for this route.
  
```
$x = (Get-CsPstnUsage).Usage
New-CsVoiceRoute -Identity Route1 -PstnUsages @{add=$x}

```

## Detailed Description

Use this cmdlet to create a new voice route. All voice routes are created at the Global scope. However, multiple global voice routes can be defined. This is accomplished through the Identity parameter, which requires a unique route name.
  
Voice routes are associated with voice policies through PSTN usages. A voice route includes a regular expression that identifies which phone numbers will be routed through a given voice route: phone numbers matching the regular expression will be routed through this route.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A name that uniquely identifies the voice route. Voice routes can be defined only at the global scope, so the identity is simply the name you want to give the route. (You can have spaces in the route name, for instance Test Route, but you must enclose the full string in double quotes in the call to the **New-CsVoiceRoute** cmdlet.) <br/> If Identity is specified, the Name must be left blank. The value of the Identity will be assigned to the Name.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |The unique name of the voice route. If this parameter is set, the value will be automatically applied to the voice route Identity. You cannot specify both an Identity and a Name.  <br/> |
| _AlternateCallerId_ <br/> |Optional  <br/> |System.String  <br/> |If the SuppressCallerId parameter is set to True, the value of the AlternateCallerId parameter will be displayed to receiving parties rather than the caller's actual number. This number should be a valid number and could be used to represent a division within an organization, such as Support or Human Resources.  <br/> If the SuppressCallerId parameter is set to False, the AlternateCallerId parameter is ignored.  <br/> This value must match the regular expression (\+)?[1-9]\d\*(;ext=[1-9]\d\*)?. In other words, the value can begin with a plus sign (+) but doesn't need to; must consist of any number of digits; and may be followed by an extension that begins with ;ext= followed by any number of digits. (Note that if you include an extension the string must be placed within double quotes.)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of what this voice route is for.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _NumberPattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that specifies the phone numbers to which this route applies. Numbers matching this pattern will be routed according to the rest of the routing settings.  <br/> Default: [0-9]{10}  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |A number could resolve to multiple voice routes. The priority determines the order in which the routes will be applied if more than one route is possible.  <br/> |
| _PstnGatewayList_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |In Skype for Business Server 2015 a Mediation Server can be associated with multiple gateways. This parameter contains a list of gateways associated with this voice route. Each member of this list must be the service Identity of the PSTN gateway or Mediation Server. The value can refer to a Mediation Server only if the Mediation Server is configured for Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2. For Skype for Business Server 2015, a PSTN gateway must be used. The service Identity is a string in the format \<ServiceRole\>:\<FQDN\>, where ServiceRole is the name of the service role (PSTNGateway), and FQDN is the fully qualified domain name (FQDN) of the pool or the IP address of the server. For example, PSTNGateway:redmondpool.litwareinc.com. Service identities can be retrieved by calling the command Get-CsService | Select-Object Identity.  <br/> By default this list is empty. However, if you leave this parameter blank when creating a new voice route, you'll receive a warning message.  <br/> |
| _PstnUsages_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of PSTN usages (such as Local, Long Distance, etc.) that can be applied to this voice route. The PSTN usage must be an existing usage. (PSTN usages can be retrieved by calling the **Get-CsPstnUsage** cmdlet.) <br/> By default this list is empty. However, if you leave this parameter blank when creating a new voice route, you'll receive a warning message.  <br/> |
| _SuppressCallerId_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether a caller's ID will be revealed on outbound calls. If this parameter is set to True, caller ID will be suppressed. In place of the actual ID, the value of the AlternateCallerId will be displayed. When SuppressCallerId is set to True, a value for AlternateCallerId must be supplied.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route.
  
## See also

#### 

[Remove-CsVoiceRoute](remove-csvoiceroute.md)
  
[Set-CsVoiceRoute](set-csvoiceroute.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)
  
[Test-CsVoiceRoute](test-csvoiceroute.md)
  
[Get-CsPstnUsage](get-cspstnusage.md)
  
[Get-CsService](get-csservice.md)

