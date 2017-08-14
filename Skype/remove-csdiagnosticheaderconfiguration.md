---
title: Remove-CsDiagnosticHeaderConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: d71b79f1-49f2-4a6c-8b3e-ca909e8d5f49
---


# Remove-CsDiagnosticHeaderConfiguration
[]
Removes one or more of the diagnostic header configuration setting collections currently in use in your organization. Diagnostic header configuration settings determine whether SIP messages are accompanied by header information that can be useful in troubleshooting and error reporting. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsDiagnosticHeaderConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the diagnostic header configuration settings that have the Identity site:Redmond are removed. 
  
    
    

```

Remove-CsDiagnosticHeaderConfiguration -Identity site:Redmond
```


### EXAMPLE 2

The command shown in Example 2 deletes all the diagnostic header configuration settings that have been applied at the service scope. To do this, the command first calls the **Get-CsDiagnosticHeaderConfiguration** cmdlet and the Filter parameter. The filter value "service:*" limits the returned data to those settings where the Identity begins with the characters "service:". This filtered collection is then piped to the **Remove-CsDiagnosticHeaderConfiguration** cmdlet, which deletes each item in the collection.
  
    
    

```
Get-CsDiagnosticHeaderConfiguration -Filter service:* | Remove-CsDiagnosticHeaderConfiguration
```


### EXAMPLE 3

Example 3 deletes all the diagnostic header configuration settings that allow sending to external networks. To do this, the command first uses the **Get-CsDiagnosticHeaderConfiguration** cmdlet to return a collection of all the diagnostic header settings currently in use. This collection is piped to the **Where-Object** cmdlet, which picks out only those settings where the SendToExternalNetworks property is equal to True. These settings are then piped to the **Remove-CsDiagnosticHeaderConfiguration** cmdlet, which deletes each setting that allows sending to external networks.
  
    
    

```
Get-CsDiagnosticHeaderConfiguration | Where-Object {$_.SendToExternalNetworks -eq $True} | Remove-CsDiagnosticHeaderConfiguration
```


## Detailed Description

Administrators have the option of attaching an ms-diagnostic header to each SIP message sent in their organization. This message (which is not visible to end users) contains information that might be useful in troubleshooting connection problems or in reporting errors. For example, the diagnostic header might contain error codes that enable the client application to take a predetermined course of action should a specific situation arise.
  
    
    
For SIP messages sent within your internal network, there's little reason not to include these diagnostic headers: they have a minimal impact on message size and can be an invaluable tool for administrators trying to troubleshoot connectivity problems. However, diagnostic headers also contain information -- such as the fully qualified domain names (FQDNs) of your SIP servers -- that you might not want to make available to people outside the internal network. Because of this, the diagnostic header configuration settings enable you to decide whether you want diagnostic headers sent to users on external networks (such as users in a federated domain) and/or to outside users. (Outside users are users who have connected from outside the internal network and have not yet been authenticated.) 
  
    
    
Alternatively, you can create custom settings at the site scope or at the service scope (for the Edge Server or Registrar service). That way, you can choose to include diagnostic headers on messages sent from one site, or through one Edge Server, while disallowing headers on messages sent from other sites or through other Edge Servers.
  
    
    
Any new collections you create (at either the site or the service scope) can later be removed by using the **Remove-CsDiagnosticHeaderConfiguration** cmdlet. You can also run this cmdlet against the global collection. In that case, however, the global collection will not be removed because you can't remove the global collection. Instead, the two properties contained in the global collection -- SendToExternalNetworks and SendToOutsideUnauthenticatedUsers -- will be reset to their default values (which, in each case, is False).
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the diagnostic header configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`. To remove settings configured at the service scope, use syntax similar to this:  `-Identity "service:EdgeServer:atl-edge-001.litwareinc.com"`.  <br/> The **Remove-CsDiagnosticHeaderConfiguration** cmdlet can also be run against the global configuration settings; in that case, use this syntax: `-Identity global`. Note, however, that the global settings will not actually be removed; instead, the properties found in the global settings will be reset to their default values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings object. The **Remove-CsDiagnosticHeaderConfiguration** cmdlet accepts pipelined instances of the diagnostic header settings object.
  
    
    

## Return Types

None. Instead, the **Remove-CsDiagnosticHeaderConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)
  
    
    
 [New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)
  
    
    
 [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)
