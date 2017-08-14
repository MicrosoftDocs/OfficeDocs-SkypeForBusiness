---
title: New-CsDiagnosticConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9028d9c1-e812-4055-bdf0-59cb83c6f50f
---


# New-CsDiagnosticConfiguration
[]
Creates new diagnostic configuration settings. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsDiagnosticConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Filter <Filter>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LogAllSipHeaders <$true | $false>] [-LoggingShare <String>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 creates a new collection of diagnostic configuration settings for the Redmond site. 
  
    
    

```

New-CsDiagnosticConfiguration -Identity site:Redmond
```


### EXAMPLE 2

The commands shown in Example 2 create a new diagnostics filter and then assign that filter to a new collection of diagnostic settings. To carry out this task, the first command calls the **New-CsDiagnosticsFilter** cmdlet to create an in-memory-only diagnostics filter; this command adds the FQDN fabrikam.com and the URI sip:user@fabrikam.com to the filter. The command also sets the Enabled property to True ($True) in order to activate the filter. The resulting virtual filter is then stored in the variable $x.
  
    
    
In command 2, the **New-CsDiagnosticConfiguration** cmdlet is used to create a new diagnostic configuration settings collection for the Redmond site. These new settings will use the diagnostic filter stored in the variable $x.
  
    
    



```
$x = New-CsDiagnosticsFilter -Fqdn fabrikam.com -Uri "sip:user@fabrikam.com" -Enabled $False

New-CsDiagnosticConfiguration -Identity site:Redmond -Filter $x
```


### EXAMPLE 3

The commands shown in Example 3 demonstrate how you can create diagnostic configuration settings that initially exist only in memory. To do this, the first command calls the **New-CsDiagnosticConfiguration** cmdlet along with two parameters: Identity (which specifies the Identity for the settings) and InMemory, which indicates that the new settings should be created in memory only. The resulting object is stored in the variable $x.
  
    
    
After the virtual settings have been created, the second command is used to configure the LoggingShare property to the UNC path \\\\atl-fs-001\\logs. The final command is then used to transform the virtual diagnostic configuration settings into an actual collection of settings applied to the Redmond site. Note that this final command is mandatory. If you do not call the **Set-CsDiagnosticConfiguration** cmdlet, no settings will be applied to the Redmond site, and the virtual settings will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  
    
    



```

$x = New-CsDiagnosticConfiguration -Identity site:Redmond -InMemory
$x.LoggingShare = "\\\\atl-fs-001\\logs"
Set-CsDiagnosticConfiguration -Instance $x
```


## Detailed Description

If you enable logging for Skype for Business Server 2015 then, by default, traffic traveling to or from any domain or URI is included in those log files. This ensures that as much information as possible is recorded in the log files.
  
    
    
However, this can occasionally result in too much information. For example, if you are experiencing connectivity problems with a particular domain, you might want to limit logging to traffic between your network and that domain; that makes it easier for you to identify the relevant records and, in turn, might make it easier for you to diagnose and correct the problem.
  
    
    
Diagnostic configuration settings make it possible for you to specify the domains or URIs that will be recorded in the log files; for example, you can log only the traffic to or from specified domains. Skype for Business Server 2015 enables you to create diagnostic configuration settings at the site scope. In turn, this enables you to apply different settings to, say, the Redmond site than you do on your other sites.
  
    
    
Note that you cannot create diagnostic configuration settings at the global scope; that's because the global scope already hosts these settings. Likewise, you cannot create a new settings collection at the site scope if the specified site already contains diagnostic configuration settings. For example, your command will fail if you try to create a new collection for the Redmond site and that site already hosts diagnostic configuration settings.
  
    
    

  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the diagnostics configuration settings to be created. Because new settings can only be created at the site scope you must use syntax similar to this:  `-Identity "site:Redmond"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Filter_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter  <br/> |Collection of domains and URIs whose traffic will be logged if diagnostic filtering is enabled. The Filter property consists of three separate items:  <br/> Fqdn - Collection of domains to be included in the filter. (More technically, this is the host portion of a SIP address.) For example a fully qualified domain name (FQDN) might look like this: fabrikam.com. Alternatively, you can use wildcards to represent multiple domains: *.fabrikam.com. You can include more than one domain in a single filter.  <br/> Uri - Collection of URIs to be included in the filter. (The Uri is the user@host portion of a SIP address.) A Uri can consist of any of the following patterns: user@fabrikam.com; user@*; *@fabrikam.com. You can include multiple URIs in a single filter.  <br/> Enabled - Indicates whether or not the filter should be activated.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _LogAllSipHeaders_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False, only the core SIP headers are recorded in the logs. Setting this value to False can help reduce the size of the log files. When set to True, all SIP headers are logged.  <br/> |
| _LoggingShare_ <br/> |Optional  <br/> |System.String  <br/> |Shared folder where the diagnostic logs can be uploaded.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **New-CsDiagnosticConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsDiagnosticConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings.
  
    
    

## See also


#### 


  
    
    
 [Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)
  
    
    
 [New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)
  
    
    
 [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)
  
    
    
 [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)
