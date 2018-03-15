---
title: "Remove-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 80239fed-89ef-4ccc-be9b-d9149182d0c3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsRoutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Resets the routing configuration to its default settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example resets the Global (and only) routing configuration to the default settings. This action deletes all defined voice routes, so we added the Confirm parameter in order to receive a prompt asking whether we really want to perform this action before the removal takes place.
  
```
Remove-CsRoutingConfiguration -Identity Global -Confirm
```

## Detailed Description
<a name="sectionSection1"> </a>

Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet removes the global (and only) routing configuration, which is a container for all voice routes defined for a Lync Server deployment. "Removing" the routing configuration doesn't actually remove it; the Global (and only) instance is still there. However, it does set the list of voice routes to the default settings. 
  
WARNING: Removing the routing configuration (in other words, setting the list of voice routes to the default) deletes all defined voice routes for a Lync Server deployment and replaces them with a single route with default settings.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsRoutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration to remove. This value must be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings object. Accepts pipelined input of a routing configuration object.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet removes (resets) an object of type Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

