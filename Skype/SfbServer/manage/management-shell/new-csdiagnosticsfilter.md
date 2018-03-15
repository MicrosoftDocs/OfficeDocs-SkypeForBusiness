---
title: "New-CsDiagnosticsFilter"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f1af92b1-4d1f-4eb3-9874-7fa6f6ae39c5
description: "Creates a new diagnostic filter to be used with diagnostic configuration settings. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010."
---

# New-CsDiagnosticsFilter
 
Creates a new diagnostic filter to be used with diagnostic configuration settings. Diagnostic configuration settings are used to determine whether traffic to or from a given domain or Uniform Resource Identifier (URI) is recorded in your Skype for Business Server 2015 log files. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsDiagnosticsFilter [-Enabled <$true | $false>] [-ExcludeConferenceMessages <$true | $false>] [-ExcludePresenceNotifications <$true | $false>] [-ExcludeRegisterMessages <$true | $false>] [-ExcludeSubscribeMessages <$true | $false>] [-ExcludeSuccessfulRequests <$true | $false>] [-Fqdn <PSListModifier>] [-Uri <PSListModifier>]

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 use the **New-CsDiagnosticsFilter** cmdlet to create a new diagnostic filter and then assign that filter to the global diagnostic configuration settings. To carry out this task, the first command calls the **New-CsDiagnosticsFilter** cmdlet to create an in-memory-only diagnostic filter. This filter adds the FQDN fabrikam.com and the URI user@fabrikam.com to the filter. The command also sets the Enabled property to True ($True) in order to activate the filter. The resulting virtual filter is then stored in the variable $x.
  
In the second command, the **Set-CsDiagnosticConfiguration** cmdlet is used to assign the new filter to the global diagnostic configuration settings. In this case, any existing values in the Filter property will be replaced by the newly-created filter stored in $x.
  
```
$x = New-CsDiagnosticsFilter -Fqdn "fabrikam.com" -Enabled $False
Set-CsDiagnosticConfiguration -Identity global -Filter $x 
```

### EXAMPLE 2

The commands shown in Example 2 are a variation of the commands shown in Example 1; in Example 2, however, two FQDNs (fabrikam.com and contoso.com) are added to the filter's Fqdn property. To do this, both names (separated by a comma) are used as parameter values for the Fqdn parameter.
  
```
$x = New-CsDiagnosticsFilter -Fqdn "fabrikam.com","contoso.com" -Enabled $False
Set-CsDiagnosticConfiguration -Identity global -Filter $x
```

## Detailed Description

If you enable logging for Skype for Business Server 2015, then, by default, traffic traveling to or from any domain or URI is included in those log files. This ensures that as much information as possible is recorded in the log files. 
  
On the other hand, this can also result in cases of too much information. For example, if you are experiencing connectivity problems with a particular domain, you might want to limit logging to traffic between your network and that domain; that makes it easier for you to identify the relevant records and, in turn, might make it easier for you to diagnose and correct the problem. 
  
Diagnostic configuration settings make it possible for you to specify the domains or URIs that will be recorded in the log files; for example, you might want to log only the traffic to or from specified domains. In addition to the global settings, Skype for Business Server 2015 enables you to create diagnostic settings at the site scope or the service scope (for either the Edge Server or the Registrar service). In turn, this enables you to apply different settings to the Redmond site than are applied to your other sites.
  
The **New-CsDiagnosticsFilter** cmdlet enables you to add a filter to a collection of diagnostic settings. This collection contains the domains and URIs that will have their traffic recorded in the log files. When a filter is added, only information pertaining to the domains and URIs in the filter will be logged; for logging purposes, traffic from other domains and URIs will be ignored.
  
Note that the **New-CsDiagnosticsFilter** cmdlet creates in-memory-only instances of a diagnostic filter. After creating one of these virtual filters, you will then need to use either the **New-CsDiagnosticConfiguration** cmdlet or the **Set-CsDiagnosticConfiguration** cmdlet to add the filter to a collection.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not the filter should be employed. The default value is True ($True).  <br/> |
| _ExcludeConferenceMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, information about conference messages (that is, any message with a conference URI in its To or From header) will not be recorded in the log files. The default value is False.  <br/> |
| _ExcludePresenceNotifications_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, information about presence notifications (that is, any message that uses the NOTIFY or BENOTIFY method) will not be recorded in the log files. The default value is False.  <br/> |
| _ExcludeRegisterMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, information about client registrations (that is, any message that uses the REGISTER method) will not be recorded in the log files. The default value is False.  <br/> |
| _ExcludeSubscribeMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, information about client subscriptions (that is, any message that uses the SUBSCRIBE method) will not be recorded in the log files. The default value is False.  <br/> |
| _ExcludeSuccessfulRequests_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True. Information about successful SIP requests will not be recorded in the log files. Instead, only information about unsuccessful requests will be saved.  <br/> |
| _Fqdn_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of domains to be included in the filter. (More technically, these domains represent the host portion of a SIP address.) For the FQDN property you can use a fully qualified domain name (FQDN) like this: fabrikam.com. Alternatively, you can use wildcards to represent multiple domains: \*.fabrikam.com. You can have more than one domain in a single filter.  <br/> |
| _Uri_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of URIs to be included in the filter. (The URI is the user@host portion of a SIP address.) A URI can consist of any of the following patterns:  <br/> user@fabrikam.com  <br/> user@\*  <br/> \*@fabrikam.com  <br/> You can include multiple URIs in a single filter.  <br/> |
| _ExcludeMidDialogRequests_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ExcludeTypingNotifications_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsDiagnosticsFilter** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsDiagnosticsFilter** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter object.
  
## See also

#### 

[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)
  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

