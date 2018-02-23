---
title: "Remove-CsProxyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 738f731c-4d62-4395-bdc3-3f5e5738f443
description: "Removes an existing collection of proxy server configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsProxyConfiguration
[]
Removes an existing collection of proxy server configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsProxyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 deletes the proxy configuration settings that have the Identity service:EdgeServer:atl-edge-litwareinc.com. 
  
```
Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com 
```

### EXAMPLE 2

In Example 2, all of the proxy configuration settings applied at the service scope are deleted. To accomplish this task, the command first calls the **Get-CsProxyConfiguration** cmdlet along with the Filter parameter. The filter value "service:*" ensures that only proxy settings that have an Identity that begins with the string value "service:" will be returned. That filtered collection is then piped to the **Remove-CsProxyConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsProxyConfiguration -Filter "service:*" | Remove-CsProxyConfiguration
```

### EXAMPLE 3

Example 3 deletes any proxy configuration settings that treat all clients as remote clients. To do this, the **Get-CsProxyConfiguration** cmdlet is first called without any parameters in order to return a collection of all the proxy server configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the TreatAllClientsAsRemote property is equal to True. This subset of proxy configuration settings is then piped to the **Remove-CsProxyConfiguration** cmdlet, which removes all the settings in the collection.
  
```
Get-CsProxyConfiguration | Where-Object {$_.TreatAllClientsAsRemote -eq $True} | Remove-CsProxyConfiguration
```

## Detailed Description

Skype for Business Server 2015 enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Skype for Business Server 2015, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope.
  
Any new proxy server settings you create can later be removed by using the **Remove-CsProxyConfiguration** cmdlet. You can also run the **Remove-CsProxyConfiguration** cmdlet against the global collection. In that case, however, the global settings will not be removed; that's because Skype for Business Server 2015 does not allow you to remove global settings. Instead, all of the properties within the global collection will be reset to their default values. For example, by default proxy server settings allow clients to use the Kerberos protocol for authentication. You can change the global settings to disable the use of Kerberos. However, if you run the **Remove-CsProxyConfiguration** cmdlet against the global collection, the property in question (UseKerberosForClientToProxyAuth) will be reset to its default value, and Kerberos will again be enabled for use as an authentication protocol.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the proxy server configuration settings to be removed; for example:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> The **Remove-CsProxyConfiguration** cmdlet can also be run against the global settings. In that case, however, the settings will not be removed. Instead, the properties within that global collection will all be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object. The **Remove-CsProxyConfiguration** cmdlet accepts pipelined instances of the proxy settings object.
  
## Return Types

None. Instead, the **Remove-CsProxyConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object.
  
## See also

#### 

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)
  
[New-CsProxyConfiguration](new-csproxyconfiguration.md)
  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

