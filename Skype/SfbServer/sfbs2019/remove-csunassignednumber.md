---
title: "Remove-CsUnassignedNumber"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 13095593-92d3-4790-99a5-5df4610652cb
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsUnassignedNumber
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing range of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUnassignedNumber -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In this example, the unassigned number settings with the Identity UNSet1 are removed.
  
```
Remove-CsUnassignedNumber -Identity UNSet1
```

### EXAMPLE 2

Example 2 removes all unassigned number settings where the name of the assigned announcement contains the string Welcome. The command begins with a call to the **Get-CsUnassignedNumber** cmdlet, which returns a collection of all unassigned number settings. This collection is then passed to the **Where-Object** cmdlet, which narrows down the collection to only those unassigned number settings with an AnnouncementName that includes (-match) the string Welcome. Finally, the narrowed-down collection is passed to the **Remove-CsUnassignedNumber** cmdlet, which removes everything left in the collection. 
  
```
Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Remove-CsUnassignedNumber
```

## Detailed Description
<a name="sectionSection1"> </a>

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Lync Server can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet removes the settings that define that routing.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsUnassignedNumber** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsUnassignedNumber"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique name for the range of unassigned numbers you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange object. Accepts pipelined input of unassigned number objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsUnassignedNumber](new-csunassignednumber.md)
  
[Set-CsUnassignedNumber](set-csunassignednumber.md)
  
[Get-CsUnassignedNumber](get-csunassignednumber.md)
  
[Get-CsAnnouncement](get-csannouncement.md)
  
[Get-CsExUmContact](get-csexumcontact.md)

