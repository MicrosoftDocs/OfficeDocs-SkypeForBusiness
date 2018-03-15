---
title: "Remove-CsProxyConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 738f731c-4d62-4395-bdc3-3f5e5738f443
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsProxyConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing collection of proxy server configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsProxyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

Lync Server enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Lync Server, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope.
  
Any new proxy server settings you create can later be removed by using the **Remove-CsProxyConfiguration** cmdlet. You can also run the **Remove-CsProxyConfiguration** cmdlet against the global collection. In that case, however, the global settings will not be removed; that's because Lync Server does not allow you to remove global settings. Instead, all of the properties within the global collection will be reset to their default values. For example, by default proxy server settings allow clients to use the Kerberos protocol for authentication. You can change the global settings to disable the use of Kerberos. However, if you run the **Remove-CsProxyConfiguration** cmdlet against the global collection, the property in question (UseKerberosForClientToProxyAuth) will be reset to its default value, and Kerberos will again be enabled for use as an authentication protocol. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsProxyConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsProxyConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the proxy server configuration settings to be removed; for example: -Identity "service:Registrar:atl-cs-001.litwareinc.com".  <br/> The **Remove-CsProxyConfiguration** cmdlet can also be run against the global settings. In that case, however, the settings will not be removed. Instead, the properties within that global collection will all be reset to their default values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object. The **Remove-CsProxyConfiguration** cmdlet accepts pipelined instances of the proxy settings object. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Remove-CsProxyConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)
  
[New-CsProxyConfiguration](new-csproxyconfiguration.md)
  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

