---
title: "Remove-CsUnassignedNumber"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 13095593-92d3-4790-99a5-5df4610652cb
description: "Removes an existing range of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsUnassignedNumber
 
Removes an existing range of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUnassignedNumber -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

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

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Skype for Business Server 2015 can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet removes the settings that define that routing.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique name for the range of unassigned numbers you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange object. Accepts pipelined input of unassigned number objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.
  
## See also

#### 

[New-CsUnassignedNumber](new-csunassignednumber.md)
  
[Set-CsUnassignedNumber](set-csunassignednumber.md)
  
[Get-CsUnassignedNumber](get-csunassignednumber.md)
  
[Get-CsAnnouncement](get-csannouncement.md)
  
[Get-CsExUmContact](get-csexumcontact.md)

