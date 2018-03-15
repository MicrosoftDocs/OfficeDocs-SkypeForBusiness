---
title: "Get-CsPstnUsage"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9dc82b88-303b-4678-8298-0dbc769f6781
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPstnUsage
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about public switched telephone network (PSTN) usage records used in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This command returns the list of global PSTN usages available within the organization.
  
```
Get-CsPstnUsage
```

### EXAMPLE 2

The command in this example returns a list of all defined PSTN usages, with one usage listed on each line of output. Calling the **Get-CsPstnUsage** cmdlet by itself returns the Identity and the Usage list. If the Usage list contains more than three or four entries, the list will be abbreviated in the output, similar to this: 
  
Usage : {Internal, Local, Long Distance, International...}
  
Use the command in this example to display only a list of usages. The output will be similar to this:
  
Internal
  
Local
  
Long Distance
  
International
  
Restricted
  
```
(Get-CsPstnUsage).Usage
```

### EXAMPLE 3

This command returns all the PSTN usage names that have the string "tern" somewhere within the name. For example, this command will return "Internal" and "International" but not "Local" or "Long Distance".
  
The first part of this command is the **Get-CsPstnUsage** cmdlet within parentheses, which means the first thing that happens is for all the PSTN usages to be retrieved. The .Usage property returns only the usage information for the PSTN usages, not the Identity. This list of usages is then piped to the **ForEach-Object** cmdlet, which looks at the usage strings one at a time. The If statement compares the current usage string to the string "*tern*" (the * are wildcards) and displays any occurrence that matches that pattern. 
  
```
(Get-CsPstnUsage).Usage | ForEach-Object {if ($_ -like "*tern*") {$_}}
```

## Detailed Description
<a name="sectionSection1"> </a>

PSTN usages are string values that are used for call authorization. A PSTN usage links a voice policy to a route. The **Get-CsPstnUsage** cmdlet retrieves the list of all PSTN usages available within an organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPstnUsage** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPstnUsage"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |The Filter parameter allows you to retrieve only those PSTN usages with an Identity matching a particular wildcard string. However, the only Identity available to PSTN usages is Global, so this parameter is not useful for this cmdlet.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The level at which these settings are applied. The only identity that can be applied to PSTN usages is Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the PSTN usage information from the local data store rather than the main Central Management store.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsPstnUsage** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PSTNUsages object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsPstnUsage](set-cspstnusage.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

