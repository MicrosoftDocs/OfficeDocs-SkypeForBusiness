---
title: "Remove-CsDiagnosticConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b15293bf-d0d1-4322-ab1d-10b54636746a
description: "Removes one or more of the diagnostic configuration settings collections currently in use in your organization. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsDiagnosticConfiguration
 
Removes one or more of the diagnostic configuration settings collections currently in use in your organization. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsDiagnosticConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 deletes the diagnostic configuration settings that have the Identity site:Redmond.
  
```
Remove-CsDiagnosticConfiguration -Identity site:Redmond
```

### EXAMPLE 2

The command shown in Example 2 deletes all the diagnostic configuration settings that have been configured at the site scope. To do this, the command calls the **Get-CsDiagnosticConfiguration** cmdlet along with the Filter parameter; the filter value "site:*" limits the returned data to settings where the Identity begins with the characters "site:". The filtered collection is then piped to the **Remove-CsDiagnosticConfiguration** cmdlet, which removes each item in that collection.
  
```
Get-CsDiagnosticConfiguration -Filter site:* | Remove-CsDiagnosticConfiguration
```

### EXAMPLE 3

In Example 3, the command deletes all the diagnostic configuration settings currently in use in the organization. To perform this task, the **Get-CsDiagnosticConfiguration** cmdlet is first called without any parameters in order to return a collection of all the diagnostic configuration settings currently in use in the organization. These items are then piped to the **Remove-CsDiagnosticConfiguration** cmdlet, which removes each item in the collection.
  
```
Get-CsDiagnosticConfiguration | Remove-CsDiagnosticConfiguration
```

## Detailed Description

If you enable logging for Skype for Business Server 2015, then, by default, traffic traveling to or from any domain or URI is included in those log files. This ensures that as much information as possible is recorded in the log files. 
  
However, this can occasionally result in too much information. For example, if you are experiencing connectivity problems with a particular domain, you might want to limit logging to traffic between your network and that domain; that makes it easier for you to identify the relevant records and, in turn, might make it easier for you to diagnose and correct the problem.
  
Diagnostic configuration settings make it possible for you to specify the domains or URIs that will be recorded in the log files; if a diagnostic filter is enabled then only traffic to or from the specified domains will be logged. Skype for Business Server 2015 enables you to create diagnostic configuration settings, and apply diagnostic filters, at the site scope. In turn, this enables you to apply filtering to, say, the Redmond site while leaving filtering disabled on your other sites.
  
You can use the ** Remove-CsDiagnosticConfiguration** cmdlet to remove any of the diagnostic configuration settings you have created at the site scope. The **Remove-CsDiagnosticConfiguration** cmdlet can also be run against the global diagnostic configuration settings. In that case, however, the collection will not be deleted; that's because Skype for Business Server 2015 does not allow you to delete global collections. Instead, removing a global collection causes the properties in that collection to be reset to their default values. That means that all the filters added to that collection will be removed.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the diagnostic configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`.  <br/> The **Remove-CsDiagnosticConfiguration** cmdlet can also be run against the global configuration settings; in that case, use this syntax: `-Identity global`. However, the global settings will not actually be removed; instead, the properties found in the global settings will be reset to their default values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings object. The **Remove-CsDiagnosticConfiguration** cmdlet accepts pipelined instances of the diagnostic filter settings object.
  
## Return Types

None. Instead, the **Remove-CsDiagnosticConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings object.
  
## See also

#### 

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)
  
[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)
  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

