---
title: "Get-CsUnassignedNumber"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a8e5cfc1-e7a0-4917-9cd9-f541fedb3a61
description: "Retrieves one or more ranges of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsUnassignedNumber
[]
Retrieves one or more ranges of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns a collection of all the unassigned numbers configured for use in your organization.
  
```
Get-CsUnassignedNumber
```

### EXAMPLE 2

In Example 2, the Identity parameter is used to limit the retrieved data to unassigned numbers that have the Identity UNSet1. Because identities must be unique, this command will return only the specified unassigned number range.
  
```
Get-CsUnassignedNumber -Identity UNSet1
```

### EXAMPLE 3

This example uses the Filter parameter to return a collection of all the unassigned number settings with Identity values that include the string Redmond. For example, this command would return unassigned number setting with identities such as Redmond Numbers, Unassigned Redmond Numbers, UNRedmond, etc.
  
```
Get-CsUnassignedNumber -Filter *Redmond*
```

### EXAMPLE 4

In Example 4, the **Get-CsUnassignedNumber** cmdlet and the **Where-Object** cmdlet are used to retrieve a collection of all the unassigned number settings that include the word Welcome in the name of the Announcement. To do this, the command first uses the **Get-CsUnassignedNumber** cmdlet to retrieve all the unassigned number settings. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to unassigned numbers that have the word Welcome somewhere in the name of the assigned announcement.
  
```
Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"}
```

## Detailed Description

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Skype for Business Server 2015 can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet retrieves one or more unassigned number ranges that define that routing.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Performs a wildcard search that allows you to narrow down your results to only those unassigned number settings whose identities match the given wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique name of the unassigned number range to retrieve.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the unassigned number information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Returns an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.
  
## See also

#### 

[New-CsUnassignedNumber](new-csunassignednumber.md)
  
[Remove-CsUnassignedNumber](remove-csunassignednumber.md)
  
[Set-CsUnassignedNumber](set-csunassignednumber.md)

