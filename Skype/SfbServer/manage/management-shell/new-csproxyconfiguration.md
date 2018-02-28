---
title: "New-CsProxyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5133470e-1d77-4958-8844-a091336b2a3c
description: "Creates a new collection of proxy configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# New-CsProxyConfiguration
[]
Creates a new collection of proxy configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsProxyConfiguration -Identity <XdsIdentity> [-AcceptClientCompression <$true | $false>] [-AcceptServerCompression <$true | $false>] [-AllowPartnerPollingSubscribes <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisableNtlmFor2010AndLaterClients <$true | $false>] [-DnsCacheRecordCount <UInt32>] [-EnableLoggingAllMessageBodies <$true | $false>] [-EnableWhiteSpaceKeepAlive <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LoadBalanceEdgeServers <$true | $false>] [-LoadBalanceInternalServers <$true | $false>] [-MaxClientCompressionCount <UInt32>] [-MaxClientMessageBodySizeKb <UInt32>] [-MaxKeepAliveInterval <UInt32>] [-MaxServerCompressionCount <UInt32>] [-MaxServerMessageBodySizeKb <UInt32>] [-OutgoingTlsCount <UInt32>] [-Realm <IRealmChoice>] [-RequestServerCompression <$true | $false>] [-SpecialConfigurationList <String>] [-TestFeatureList <String>] [-TestParameterList <String>] [-TreatAllClientsAsRemote <$true | $false>] [-UseCertificateForClientToProxyAuth <$true | $false>] [-UseKerberosForClientToProxyAuth <$true | $false>] [-UseNtlmForClientToProxyAuth <$true | $false>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 creates a new collection of proxy configuration settings for the service EdgeServer:atl-edge-001.litwareinc.com. These new settings use all the default proxy server property values except for two: RequestServerCompression, which is set to True; and MaxClientMessageBodySizeKb, which is set to 256. Note that this command will fail if proxy server settings have already been configured for the service EdgeServer:atl-edge-001.litwareinc.com.
  
```
New-CsProxyConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -RequestServerCompression $True -MaxClientMessageBodySizeKb 256
```

### EXAMPLE 2

The commands shown in Example 2 demonstrate how you can create a collection of proxy server settings that initially exist only in memory. To do this, the first command calls the **New-CsProxyConfiguration** cmdlet along with two parameters: Identity (which specifies the Identity for the settings) and InMemory, which indicates that the new settings should be created in memory only. The resulting object is stored in the variable $x.
  
After these virtual settings have been created, commands 2 and 3 are used to modify the values of the RequestServerCompression and MaxClientMessageBodySizeKb properties, respectively. Finally, command 4 is used to transform the virtual proxy server configuration settings into an actual collection of settings applied to the service EdgeServer:atl-edge-001.litwareinc.com. This final command is mandatory. If you do not call the **Set-CsProxyConfiguration** cmdlet, no settings will be applied to EdgeServer:atl-edge-001.litwareinc.com and the virtual settings will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  
```
$x = New-CsProxyConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -InMemory
$x.RequestServerCompression = $True 
$x.MaxClientMessageBodySizeKb = 256
Set-CsProxyConfiguration -Instance $x
```

## Detailed Description

Skype for Business Server 2015 enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Skype for Business Server 2015, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope. These new collections are created by using the **New-CsProxyConfiguration** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the proxy server configuration settings to be created. Proxy server configuration settings can only be created at the service scope, and only for the Edge Server and Registrar services. You cannot create settings at the global scope; likewise, you cannot create settings at the service scope if the service in question already hosts a collection of proxy server settings. For example, if the service Registrar:atl-cs-001.litwareinc.com already hosts proxy server settings, then any command that attempts to create new settings for that service will fail.  <br/> To specify the Identity for your new proxy server settings, use syntax similar to this:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> |
| _AcceptClientCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the proxy server will accept all incoming compression requests from client endpoints.  <br/> |
| _AcceptServerCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the proxy server will accept all incoming compression requests from other servers.  <br/> |
| _AllowPartnerPollingSubscribes_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set the True, partner applications are allowed to periodically poll the service for state changes. The default value is False ($False).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisableNtlmFor2010AndLaterClients_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users logging on from Skype for Business must use the Kerberos protocol for authentication. The default value is False.  <br/> |
| _DnsCacheRecordCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of records that can be maintained in the DNS record cache. The default value is 3000.  <br/> |
| _EnableLoggingAllMessageBodies_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Microsoft Lync Server will log the actual content of all instant messages. For privacy reasons, message content is typically deleted and only information about the communicating endpoints is included in the log files.  <br/> The default value is False.  <br/> |
| _EnableWhiteSpaceKeepAlive_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the proxy server expects clients to periodically send a "whitespace message" (an empty message with no content) to indicate that the connection is still active.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _LoadBalanceEdgeServers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When True, software load balancing is employed for requests to Edge Servers. The default value is True ($True).  <br/> |
| _LoadBalanceInternalServers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When True, software load balancing is employed for requests to Registrars and other internal servers. The default value is true ($True).  <br/> |
| _MaxClientCompressionCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of client-to-server connections that can be compressed at any given time; additional connections beyond this limit will not be compressed. The compression count can be set to any integer value between 0 and 65535, inclusive. The default value is 15000.  <br/> |
| _MaxClientMessageBodySizeKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum-allowed size (in kilobytes) for the body of a message sent from a client endpoint. The default value is 128, meaning that messages with a body size larger than 128 KB will be rejected. The client message body size can be set to any integer value between 64 and 256, inclusive.  <br/> |
| _MaxKeepAliveInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the amount of time (in minutes) that can elapse before the server verifies that the connection with the client is still valid. The default value is 20 minutes.  <br/> |
| _MaxServerCompressionCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of server-to-server connections that can be compressed at any given time; additional connections beyond this limit will not be compressed. The server compression count can be set to any integer value between 0 and 65535, inclusive. The default value is 1024.  <br/> |
| _MaxServerMessageBodySizeKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum-allowed size (in kilobytes) for the body of a message sent from another server. The default value is 5000, meaning that messages with a body size larger than 5000 KB will be rejected. The server message body size can be set to any integer value between 1000 and 20000, inclusive.  <br/> |
| _OutgoingTlsCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of Transport Layer Security (TLS) connections that can be used for each internal server. The minimum number of TLS connections is 1, and the maximum number is 4. By default, OutgoingTlsCount is set to 4.  <br/> |
| _Realm_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.IRealmChoice  <br/> |Indicates whether or not security credentials are processed by the default proxy server realm (SIP Communications Service) or by a custom realm. Custom realms must be specified (and created) by using the **New-CsSipProxyCustom** cmdlet. <br/> |
| _RequestServerCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) the proxy server requests that compression be used on all outgoing connections to other servers.  <br/> |
| _SpecialConfigurationList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _TestFeatureList_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not currently used by Skype for Business Server 2015.  <br/> |
| _TestParameterList_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not currently used by Skype for Business Server 2015.  <br/> |
| _TreatAllClientsAsRemote_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the proxy server functions as if all client connections are external connections that pass through the Edge Server running the Access Edge service. The default value is False.  <br/> |
| _UseCertificateForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use certificates for authentication.  <br/> |
| _UseKerberosForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use the Kerberos protocol for authentication. Although Kerberos is a more secure protocol than NTLM, it cannot be used if the client belongs to a different realm than the server.  <br/> |
| _UseNtlmForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use the NTLM protocol for authentication. Although NTLM is a less secure protocol than Kerberos, NTLM can be used if the client belongs to a different domain than the server. That is not true for Kerberos authentication.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _UseCertificatePinningForInternalConnections_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsProxyConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsProxyConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object.
  
## See also

#### 

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)
  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)
  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

