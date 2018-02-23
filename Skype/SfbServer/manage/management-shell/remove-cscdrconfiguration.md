---
title: "Remove-CsCdrConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 64352746-a03c-434a-9baf-4d9cd630e9da
description: "Removes the specified collection of call detail recording (CDR) settings. CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsCdrConfiguration
[]
Removes the specified collection of call detail recording (CDR) settings. CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 uses the **Remove-CsCdrConfiguration** cmdlet to remove the CDR settings assigned to the Redmond site. Using the Identity parameter ensures that only the settings assigned to the specified site will be removed.
  
```
Remove-CsCdrConfiguration -Identity site:Redmond
```

### EXAMPLE 2

The command shown in Example 2 removes all the CDR settings that have been assigned at the site scope. To do this, the command first uses the **Get-CsCdrConfiguration** cmdlet and the Filter parameter to retrieve the appropriate CDR settings; the string value "site:*" ensures that only those settings that have an Identity that begins with the characters "site:" are returned. The filtered collection is then piped to the **Remove-CsCdrConfiguration** cmdlet, which deletes all the items in the collection.
  
```
Get-CsCdrConfiguration -Filter site:* | Remove-CsCdrConfiguration
```

### EXAMPLE 3

In Example 3, any CDR settings where the KeepCallDetailForDays property is less than 30 days are deleted. To carry out this task, the command calls the **Get-CsCdrConfiguration** cmdlet without any parameters in order to return a collection of all the CDR settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the KeepCallDetailForDays property is less than 30 days. The filtered collection is then piped to the **Remove-CsCdrConfiguration** cmdlet, which deletes each item in that collection.
  
```
Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30} | Remove-CsCdrConfiguration
```

## Detailed Description

Call detail recording (CDR) provides a way for you to track usage of Skype for Business Server 2015 capabilities such as Voice over Internet Protocol (VoIP) phone calls; instant messaging; file transfers; audio/video (A/V) conferencing; and application sharing sessions. CDR (which is available only if you have deployed the Monitoring service) keeps usage information: it logs information such as the parties involved in the call; the length of the call; and whether or not any files were transferred. (However, CDR does not make a recording of the call itself.)
  
CDR also keeps track of call error information: detailed diagnostic data for both peer-to-peer sessions and for conferencing calls.
  
As an administrator, you can determine whether or not CDR is used in your organization. If Monitoring Service has been deployed, you can easily enable or disable CDR. In addition, you can make this decision globally (in which case CDR will either be enabled or disabled throughout the organization) or on a site-by-site basis; for example, you could use CDR in the Redmond site but not use CDR in the Paris site. 
  
Site-specific settings you create by using the **New-CsCdrConfiguration** cmdlet can later be removed by using the **Remove-CsCdrConfiguration** cmdlet. When you remove site-specific settings, then CDR for the affected site will automatically be governed by the global CDR configuration settings.
  
You can also run the **Remove-CsCdrConfiguration** cmdlet against the global CDR settings. However, because the global settings cannot be removed, they will instead be reset to their default values. For example, suppose, you set the value of the KeepCallDetailForDays property in the global settings to 90. If you run the **Remove-CsCdrConfiguration** cmdlet against the global settings, that property will be reset to its default value of 60.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the CDR configuration settings to be removed. To "remove" the global settings, use this syntax:  `-Identity global`. (Note, again, that you cannot actually remove the global settings; all you can do is reset the properties to their default values.) To remove settings from the site scope, use syntax similar to this:  `-Identity site:Redmond`. You cannot use wildcards when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. The **Remove-CsCdrConfiguration** cmdlet accepts pipelined input of CDR configuration objects.
  
## Return Types

None. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings object.
  
## See also

#### 

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)
  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)
  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

