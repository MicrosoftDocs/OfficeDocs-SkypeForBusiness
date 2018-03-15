---
title: "Get-CsProxyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e4836619-026f-4df0-adbd-aa5216e36368
description: "Returns information about the proxy server configuration settings currently in use in your organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsProxyConfiguration
 
Returns information about the proxy server configuration settings currently in use in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the proxy configuration settings currently in use in the organization. This is done by calling the **Get-CsProxyConfiguration** cmdlet without any parameters.
  
```
Get-CsProxyConfiguration
```

### EXAMPLE 2

In Example 2, information about the proxy configuration settings that have the Identity service:EdgeServer:atl-cs-001.litwareinc.com is returned. Because Identities must be unique, this command will never return more than one collection of settings.
  
```
Get-CsProxyConfiguration -Identity "service:EdgeServer:atl-cs-001.litwareinc.com"
```

### EXAMPLE 3

Example 3 returns information about all of the proxy settings that have been configured at the service scope. To do this, the command calls the **Get-CsProxyConfiguration** cmdlet along with the Filter parameter; the filter value "service:*" ensures that only those settings that have an Identity that begins with the string value "service:" will be returned.
  
```
Get-CsProxyConfiguration -Filter "service:*"
```

### EXAMPLE 4

Example 4 returns information about the proxy configuration settings that do not allow the use of client certificates as an authentication mechanism. To carry out this task, the command first uses the **Get-CsProxyConfiguration** cmdlet to return a collection of all the proxy configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the UseCertificateForClientToProxyAuth property is equal to False.
  
```
Get-CsProxyConfiguration | Where-Object {$_.UseCertificateForClientToProxyAuth -eq $False}
```

### EXAMPLE 5

Example 5 returns all the proxy configuration settings where the maximum body size for a client message is less than 5000 kilobytes. To do this, the command first calls the **Get-CsProxyConfiguration** cmdlet without any parameters; this returns a collection of all the proxy configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out those settings where the MaxClientMessageBodySizeKb property is less than 5000 kilobytes.
  
```
Get-CsProxyConfiguration | Where-Object {$_.MaxClientMessageBodySizeKb -lt 5000}
```

## Detailed Description

Skype for Business Server 2015 enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Skype for Business Server 2015, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope.
  
The **Get-CsProxyConfiguration** cmdlet enables you to return information about any of the proxy server configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the proxy configuration settings to be returned. For example, this syntax returns all the settings configured at the service scope:  <br/>  `-Filter "service:*"` <br/> You cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the proxy server configuration settings to be returned. To return the global settings, use this syntax:  <br/>  `-Identity global` <br/> To return settings configured at the service scope, use syntax similar to this:  <br/>  `-Identity "service:EdgeServer:atl-cs-001.litwareinc.com"` <br/> Note that you cannot use wildcards when specifying an Identity. If you want to (or need to) use wildcards, use the Filter parameter instead.  <br/> If this parameter is not included, the **Get-CsProxyConfiguration** cmdlet returns all of the proxy server settings currently in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the proxy configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsProxyConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsProxyConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object.
  
## See also

#### 

[New-CsProxyConfiguration](new-csproxyconfiguration.md)
  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)
  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

