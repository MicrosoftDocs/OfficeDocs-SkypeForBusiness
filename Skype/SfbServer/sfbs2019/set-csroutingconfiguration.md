---
title: "Set-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab69c6e8-262a-4ecb-b1af-513383c494fe
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsRoutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies a list of voice routes. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

It takes several steps to modify a voice route within a routing configuration. In this example, we start by retrieving the routing configuration object by calling the **Get-CsRoutingConfiguration** cmdlet. We assign the object retrieved (there will be only one) to the variable $a. 
  
In line 2 of this example we retrieve the contents of the Route property from variable $a, which is a collection of voice route objects. We then pipe that collection to the **Where-Object** cmdlet, where we search the collection for all voice route objects with a Name matching the string LocalRoute. We assign that object to the variable $b. 
  
Next, we modify the LocalRoute voice route object by assigning the value $False to the property SuppressCallerId. By updating that object we've updated the object in variable $a. However, that object is still only in memory. As a final step, we need to save those changes by passing $a to the Instance parameter of the **Set-CsRoutingConfiguration** cmdlet. 
  
This is not the recommended way of modifying a routing configuration. To modify a routing configuration, simply change the individual voice routes with the **Set-CsVoiceRoute** cmdlet, as shown here: 
  
Set-CsVoiceRoute -Identity LocalRoute -SuppressCallerId $False
  
That one line will accomplish the same task shown in Example 1.
  
```
$a = Get-CsRoutingConfiguration
$b = $a.Route | Where-Object {$_.Name -match "LocalRoute"}
$b.SuppressCallerId = $False
Set-CsRoutingConfiguration -Instance $a
```

## Detailed Description
<a name="sectionSection1"> </a>

Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). With this cmdlet you can modify the settings of any voice route defined within a Lync Server deployment.
  
The use of this cmdlet is not recommended. To modify routing configurations, modify the individual voice routes by calling the **Set-CsVoiceRoute** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsRoutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableLocationBasedRouting_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsIdentity  <br/> |The scope of the routing configuration. This must be Global.  <br/> |
| _Instance_ <br/> |Optional  <br/> |PstnRoutingSettings  <br/> |A routing configuration (Microsoft.Rtc.Management.WritablConfig.Policy.Voice.PstnRoutingSettings) object. An object of this type can be retrieved by calling the **Get-CsRoutingConfiguration** cmdlet.  <br/> |
| _Route_ <br/> |Optional  <br/> |PSListModifier  <br/> |A list of all voice routes (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route objects) defined for the Lync Server deployment.  <br/> You should modify individual voice route objects by using the **Set-CsVoiceRoute** cmdlet. That is the recommended way of modifying routes in this list.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.WritableConfig.Management.Policy.Voice.PSTNRoutingSettings object. Accepts pipelined input of a routing configuration object.
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsRoutingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
  
[Set-CsVoiceRoute](set-csvoiceroute.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

