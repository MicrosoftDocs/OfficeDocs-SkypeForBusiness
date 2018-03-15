---
title: "Set-CsDiagnosticConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 26463da9-cd6a-4ea3-961c-2570a8801cba
description: "Modifies existing diagnostic configuration settings. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsDiagnosticConfiguration
 
Modifies existing diagnostic configuration settings. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsDiagnosticConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 use the **New-CsDiagnosticsFilter** cmdlet to create a new diagnostics filter, then assign that new filter to the global diagnostic configuration settings. To carry out this task, the first command calls the **New-CsDiagnosticsFilter** cmdlet in order to create an in-memory-only diagnostics filter that uses the FQDN fabrikam.com and the URI sip:user@fabrikam.com. This "virtual" filter is then stored in the variable $x.
  
In command 2, the **Set-CsDiagnosticConfiguration** cmdlet assigns the new filter to the global diagnostic configuration settings. In this case, any existing values in the Filter property will be replaced by the newly-created filter.
  
```
$x = New-CsDiagnosticsFilter -Fqdn fabrikam.com -Uri sip:user@fabrikam.com 
Set-CsDiagnosticConfiguration -Identity global -Filter $x
```

### EXAMPLE 2

Example 2 shows how you can add a new FQDN to the Filter property of the global diagnostic configuration settings. To do this, the first command in the example uses the **Get-CsDiagnosticConfiguration** cmdlet to retrieve the value of the Filter property for the global settings. This is done by enclosing the call to the **Get-CsDiagnosticConfiguration** cmdlet in parentheses; that causes the Windows PowerShell command-line interface to run that command before it does anything else. After the global settings are returned, the value of the Filter property is extracted and stored in a variable named $x.
  
In the second command, the Add method is used to add a new FQDN (fabrikam.com) to the filter. When that's done, the final command in the example uses the **Set-CsDiagnosticConfiguration** cmdlet to save the modified diagnostics collection. The net result is that fabrikam.com will be added to any FQDNs already included in the Filter property.
  
```
$x = (Get-CsDiagnosticConfiguration -Identity global).Filter
$x.Fqdn.Add("fabrikam.com")
Set-CsDiagnosticConfiguration -Identity global -Filter $x
```

### EXAMPLE 3

The commands shown in Example 3 remove an FQDN (fabrikam.com) from the Filter property of the global diagnostic configuration settings. The first command in the example uses the **Get-CsDiagnosticConfiguration** cmdlet to retrieve the current value of the Filter property for the global settings; this value is stored in a variable named $x. After that value has been retrieved, the Remove method is used to remove the FQDN fabrikam.com. After the FQDN has been removed, the **Set-CsDiagnosticConfiguration** cmdlet is used write the modified filter (stored in the variable $x) to the global settings.
  
```
$x = (Get-CsDiagnosticConfiguration -Identity global).Filter
$x.Fqdn.Remove("fabrikam.com")
Set-CsDiagnosticConfiguration -Identity global -Filter $x
```

### EXAMPLE 4

In Example 4, all the items are removed from the Filter property of the global diagnostic configuration settings. This is done by setting the Filter property to a Null value.
  
```
Set-CsDiagnosticConfiguration -Identity global -Filter $Null
```

## Detailed Description

If you enable logging for Skype for Business Server 2015, then, by default, traffic traveling to or from any domain or URI is included in those log files. This ensures that as much information as possible is recorded in the log files.
  
However, this can occasionally result in too much information. For example, if you are experiencing connectivity problems with a particular domain, you might want to limit logging to traffic between your network and that domain; that makes it easier for you to identify the relevant records and, in turn, might make it easier for you to diagnose and correct the problem.
  
Diagnostic configuration settings make it possible for you to specify the domains or URIs that will be recorded in the log files. Skype for Business Server 2015 enables you to create diagnostic configuration settings at the site scope. In turn, this enables you to apply different settings to the Redmond site while than you do on your other sites.
  
You can use the **Set-CsDiagnosticConfiguration** cmdlet to add or remove filters from a given collection. Filters are used to indicate the domains whose traffic should be logged.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Filter_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter  <br/> |Collection of domains and URIs whose traffic will be logged. The Filter property consists of three separate items, and must be created using the **New-CsDiagnosticsFilter** cmdlet: <br/> Fqdn - Collection of domains to be included in the filter. (More technically, the host portion of a SIP address.) For example a fully qualified domain name (FQDN) might look like this: fabrikam.com. Alternatively, you can use wildcards to represent multiple domains: \*.fabrikam.com. You can include more than one domain in a single filter.  <br/> Uri - Collection of Uris to be included in the filter. (The Uri represents the user@host portion of a SIP address.) A URI can consist of any of the following patterns: user@fabrikam.com; user@\*; \*@fabrikam.com. You can include multiple Uris in a single filter.  <br/> Enabled - Indicates whether or not the filter should be activated.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the diagnostics configuration settings to be modified. To modify settings configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`. To modify the global settings, use this syntax:  `-Identity global`.  <br/> If this parameter is not specified, then the **Set-CsDiagnosticConfiguration** cmdlet will automatically modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |DiagnosticFilterSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _LogAllSipHeaders_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False, only the core SIP headers are recorded in the logs. Setting this value to False can help reduce the size of the log files. When set to True, all SIP headers are logged.  <br/> |
| _LoggingShare_ <br/> |Optional  <br/> |System.String  <br/> |Shared folder where the diagnostic logs can be uploaded.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings object. The **Set-CsDiagnosticConfiguration** cmdlet accepts pipelined instances of the diagnostic configuration settings object.
  
## Return Types

The **Set-CsDiagnosticConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings object.
  
## See also

#### 

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)
  
[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)
  
[New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)
  
[Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

