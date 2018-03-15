---
title: "Set-CsAVEdgeConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b410164b-b47d-450c-8048-983cac4be624
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsAVEdgeConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to modify configuration settings for computers running the A/V Edge service (these computers are also known as A/V Edge servers). An A/V Edge server enables internal users to share audio and video data with external users (that is, users who are not logged on to your internal network), as well as exchange files and participate in desktop sharing sessions. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsAVEdgeConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the command modifies the MaxTokenLifetime property for the global A/V Edge configuration settings. In this example, the maximum token lifetime is set to 4 hours (04 hours : 00 minutes : 00 seconds).
  
```
Set-CsAVEdgeConfiguration -Identity global -MaxTokenLifetime "04:00:00"
```

## Detailed Description
<a name="sectionSection1"> </a>

An A/V Edge server provides a way for audio and video traffic to be exchanged across an organization's firewall. Among other things, this enables users to use Lync Server across the Internet, and then exchange audio and video data with users who have logged onto the system from inside the firewall. Edge Server configuration settings can be assigned at the global scope, the site scope, and the service scope. These configuration settings enable administrators to do such things as manage the amount of time that user authentication is valid before it must be renewed, and to limit the amount of bandwidth that can be used by a single user or a single port.
  
The **Set-CsAVEdgeConfiguration** cmdlet provides a way for you to modify the A/V Edge configuration settings currently in use in your organization. However, unless instructed by Microsoft support personnel, it is recommended that administrators do not modify the default A/V Edge settings. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsAVEdgeConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsAVEdgeConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of A/V Edge configuration settings to be modified. To modify the global collection, use the following syntax: -Identity global. To modify a site collection use syntax similar to this: -Identity site:Redmond. Settings configured at the service scope should be referred to using syntax similar to this: -Identity service:EdgeServer:atl-cs-001.litwareinc.com.  <br/> |
| _Instance_ <br/> |Optional  <br/> |MediaRelaySettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaxBandwidthPerPortKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of bandwidth (in kilobits per second) that can be allocated to a single port. The maximum bandwidth can be set to any integer value between 1 and 4294967296 (4096 gigabits) per second; the default value is 3000.  <br/> |
| _MaxBandwidthPerUserKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of bandwidth (in kilobits per second) that can be allocated to any one user. The maximum bandwidth can be set to any integer value between 1 and 4294967296 (4096 gigabits) per second; the default value is 10000.  <br/> |
| _MaxTokenLifetime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time that an authentication token can be used before it expires and must be renewed. Token lifetimes are expressed using the following format: Days.Hours:Minutes:Seconds. For example, 13 days must be expressed like this, with a period (.) following the number of days, and colons (:) used to separate the hours, minutes, and seconds:  <br/> 13.00:00:00  <br/> The default value of 8 hours must be expressed like this:  <br/> 08:00:00  <br/> The minimum allowed token lifetime is 1 minute (00:01:00); the maximum allowed lifetime is 180 days (180.00:00:00).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object. The **Set-CsAVEdgeConfiguration** cmdlet accepts pipelined input of media relay settings objects. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsAVEdgeConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
  
[Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

