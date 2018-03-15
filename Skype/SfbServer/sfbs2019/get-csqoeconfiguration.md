---
title: "Get-CsQoEConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e2ed87e0-a5ae-41a2-8572-bda0070c59dc
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsQoEConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves one or more collections of Quality of Experience (QoE) settings. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsQoEConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example uses the **Get-CsQoEConfiguration** cmdlet to return a collection of all the QoE settings configured for use in your organization. 
  
```
Get-CsQoEConfiguration
```

### EXAMPLE 2

Example 2 uses the Identity parameter to ensure that the **Get-CsQoEConfiguration** cmdlet returns only the QoE settings with the Identity site:Redmond. 
  
```
Get-CsQoEConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In Example 3 the Filter parameter is used to return all the QoE settings that have been configured at the site scope. The wildcard "site:\*" returns all the QoE settings that have an Identity beginning with the string value site:. Settings that meet those criteria are settings that have been configured at the site scope.
  
```
Get-CsQoEConfiguration -Filter site:*
```

### EXAMPLE 4

Example 4 returns a collection of all the QoE settings where the KeepQoEDataForDays property is less than 30 days. To do this, the command first uses the **Get-CsQoEConfiguration** cmdlet to return a collection of all the QoE settings configured in the organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to those settings that have a KeepQoEDataForDays value of less than 30 days. 
  
```
Get-CsQoEConfiguration | Where-Object {$_.KeepQoEDataForDays -lt 30}
```

## Detailed Description
<a name="sectionSection1"> </a>

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to retrieve settings that configure QoE at the global or site level.
  
QoE is part of the Monitoring Server role; therefore Monitoring Server must be deployed on your Lync Server installation before QoE recording takes effect or any QoE data can be collected.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsQoEConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsQoEConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or multiple collections) of QoE configuration settings. To return a collection of all the settings configured at the site scope, use this syntax: -Filter site:\*. To return a collection of all the settings that have the string value "Western" somewhere in their Identity (the only property you can filter on) use this syntax: -Filter \*Western\*.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to retrieve. Possible values are global and site:\<site name\>, where \<site name\> is the name of the site in your Lync Server deployment to which you want to apply the changes.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the settings from the local replica of the Central Management store.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsQoEConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
[Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)

