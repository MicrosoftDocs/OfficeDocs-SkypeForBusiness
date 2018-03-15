---
title: "Remove-CsConferenceDisclaimer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 196252a1-2526-4944-9064-01d1846f3266
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsConferenceDisclaimer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsConferenceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 resets the property values of the global disclaimer. That means that both the disclaimer Header and Body will be set to null values, giving you a blank disclaimer.
  
```
Remove-CsConferenceDisclaimer -Identity global
```

## Detailed Description
<a name="sectionSection1"> </a>

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants when these people join conferences hosted by Lync Server. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference. Users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note that this disclaimer is only shown to users who join a conference by using a hyperlink.
  
Lync Server allows for a single, global instance of the conference disclaimer. The **Remove-CsConferenceDisclaimer** cmdlet enables you to reset your conference disclaimer: when you run this cmdlet, both the disclaimer header and the disclaimer body are set to null values. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsConferenceDisclaimer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsConferenceDisclaimer"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conference disclaimer to be removed. Although you can only have a single, global instance of the conference disclaimer, you must still use the Identity parameter when calling the **Remove-CsConferenceDisclaimer** cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object. The **Remove-CsConferenceDisclaimer** cmdlet accepts pipelined input of conference disclaimer objects. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Remove-CsConferenceDisclaimer** cmdlet resets existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object to their default property values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)
  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

