---
title: "Get-CsRoutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37a1cbc9-b8b2-423c-8ebb-7947fdcad24e
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsRoutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves the routing configuration object, which contains a list of all voice routes defined within a Lync Server deployment. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves the routing configuration. To retrieve individual voice routes, use the **Get-CsVoiceRoute** cmdlet. 
  
```
Get-CsRoutingConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet is used to retrieve the global instance that holds a list of all voice routes defined within the Lync Server deployment. To retrieve individual voice routes or to retrieve them as individual objects rather than as a list, use the **Get-CsVoiceRoute** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsRoutingConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsRoutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |There can be only one instance of this object, so this parameter does nothing.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the routing configuration to retrieve. The only possible value is Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the routing configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsRoutingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.Writable.Policy.Voice.PSTNRoutingSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)
  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

