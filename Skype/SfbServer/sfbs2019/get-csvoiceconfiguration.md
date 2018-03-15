---
title: "Get-CsVoiceConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c5e7afa3-28d3-4bf9-a2f2-c34932c9a3cd
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsVoiceConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves the voice configuration object, which contains a full list of all voice test configurations defined for the Lync Server deployment. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves the voice configuration. To retrieve the voice test configurations, use the **Get-CsVoiceTestConfiguration** cmdlet. 
  
```
Get-CsVoiceConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet is used to retrieve the global instance that holds a list of all voice test configurations defined within the Lync Server deployment. To retrieve individual voice test configurations or to retrieve them as individual objects rather than as a list, use the **Get-CsVoiceTestConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoiceConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsVoiceConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |There can only be one instance of this object, so this parameter does nothing.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the voice configuration to retrieve. The only possible value is Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)
  
[Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

