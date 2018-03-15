---
title: "Set-CsCdrConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 977f0d3e-796b-43a3-bc0c-82ea91741c52
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsCdrConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing collection of call detail recording (CDR) settings. CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 sets the time of day for purging old records. In this case the time is set to 23 (11:00 P.M. on a 24-hour clock). The Identity parameter is used to ensure that these changes are only made to the CDR settings that have the Identity site:Redmond.
  
```
Set-CsCdrConfiguration -Identity site:Redmond -PurgeHourOfDay 23 
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1. In this case, the PurgeHourOfDay property is modified for each collection of CDR configuration settings currently in use in the organization. To do this, the command first calls the **Get-CsCdrConfiguration** cmdlet without any parameters in order to return a collection of all the CDR settings currently in use. This collection is then piped to the **Set-CsCdrConfiguration** cmdlet, which takes each item in the collection and changes the value of the PurgeHourOfDay property to 11:00 PM (23). 
  
```
Get-CsCdrConfiguration | Set-CsCdrConfiguration -PurgeHourOfDay 23 
```

### EXAMPLE 3

Another variation of the command used in Example 1 is shown in Example 3. In this example, the PurgeHourOfDay property is changed for all the CDR settings that have been configured at the site scope. To perform this task, the command first calls the **Get-CsCdrConfiguration** cmdlet along with the Filter parameter; the filter value "site:*" ensures that only CDR settings that have an Identity that begins with the string value "site:" will be returned. The filtered collection is then piped to the **Set-CsCdrConfiguration** cmdlet, which changes the PurgeHourOfDay property for each item in that collection. 
  
```
Get-CsCdrConfiguration -Filter "site:*"| Set-CsCdrConfiguration -PurgeHourOfDay 23
```

## Detailed Description
<a name="sectionSection1"> </a>

Call detail recording (CDR) provides a way for you to track usage of Lync Server capabilities such as Voice over Internet Protocol (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. CDR (which is available only if you have deployed the Monitoring service) keeps usage information: it logs information such as the parties involved in the call; the length of the call; and whether or not any files were transferred. However, CDR does not make a recording of the call itself.
  
CDR also keeps track of call error information: detailed diagnostic data for both peer-to-peer sessions and for conferencing calls.
  
As an administrator, you can determine whether or not CDR is used in your organization; assuming that the Monitoring Service has been deployed, you can easily enable or disable CDR. In addition, you can make this decision globally (in which case CDR will either be enabled or disabled throughout the organization) or on a site-by-site basis. For example, you could use CDR in the Redmond site but not use CDR in the Paris site. 
  
Administrators can also manage the CDR database; for example, you can specify the number of days CDR records are maintained before they are purged from that database. Changes such as these can be made by using the **Set-CsCdrConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsCdrConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsCdrConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableCDR_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not CDR is enabled. The default value is True.  <br/> |
| _EnablePurging_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not CDR records will periodically be deleted from the CDR database. If True (the default value), records will be deleted after the time period specified by the properties KeepCallDetailForDays (for CDR records) and KeepErrorReportForDays (for CDR errors). If False, CDR records will be maintained indefinitely.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier assigned to the collection of CDR configuration settings. To refer to the global settings, use this syntax: -Identity global. To refer to a collection configured at the site scope, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcard characters when specifying an Identity.  <br/> If this parameter is omitted then the **Set-CsCdrConfiguration** cmdlet will modify the global settings.  <br/> |
| _Instance_ <br/> |Optional  <br/> |CdrSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _KeepCallDetailForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the number of days that CDR records will be kept in the CDR database; any records older than the specified number of days will automatically be deleted. (Note that purging will take only place if the EnablePurging property has been set to true.)  <br/> You can set this property to any integer value between 1 and 2562 days (approximately 7 years). The default value is 60.  <br/> |
| _KeepErrorReportForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the number of days that CDR error reports are kept; any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications such as Lync 2013.  <br/> You can set this property to any integer value between 1 and 2562 days (approximately 7 years). The default value is 60.  <br/> |
| _PurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the local time of day when expired records are deleted from the CDR database. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 A.M.) and 23 representing 11:00 P.M. Note that you can only specify the hour of the day; that means that you can schedule purging to take place at 4:00 A.M., but you cannot schedule it to take place at 4:30 A.M. or 4:15 A.M.. The default value is 2 (2:00 A.M.). It is recommended that purging take place during non-working hours.  <br/> Database purging takes place only if the EnablePurging property is set to True.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. The **Set-CsCdrConfiguration** cmdlet accepts pipelined input of call detail recording configuration objects. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsCdrConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CDRSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)
  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)
  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

