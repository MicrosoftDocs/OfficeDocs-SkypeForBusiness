---
title: "Set-CsProxyConfiguration"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 1/12/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2eb74d25-05b5-4901-aa92-eeda2f351e25
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsProxyConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing collection of proxy server configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, all the proxy configuration settings that have the Identity service:EdgeServer:atl-edge-001.litwareinc.com are modified to accept server compression. This is done by calling the **Set-CsProxyConfiguration** cmdlet and the AcceptServerCompression parameter, and by setting the parameter value to True. 
  
```
Set-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-001.litwareinc.com -AcceptServerCompression $True
```

### EXAMPLE 2

Example 2 locates all of the proxy configuration settings that accept server compression, and then modifies these settings to accept client compression as well. To do this, the command first calls the **Get-CsProxyConfiguration** cmdlet without any parameters in order to return a collection of all the proxy settings in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the AcceptServerCompression property is equal to True. The filtered collection is then piped to the **Set-CsProxyConfiguration** cmdlet, which takes each item in the collection and sets the AcceptClientCompression property to True. 
  
```
Get-CsProxyConfiguration | Where-Object {$_.AcceptServerCompression -eq $True} | Set-CsProxyConfiguration -AcceptClientCompression $True
```

### EXAMPLE 3

Example 3 shows how you can modify all of the proxy settings that have been configured at the service scope. In order to do this, the command first calls the **Get-CsProxyConfiguration** cmdlet and includes the Filter parameter; the filter value "service:*" ensures that only settings that have an Identity that begins with the string value "service:" are returned. The filtered collection is then piped to the **Set-CsProxyConfiguration** cmdlet, which takes each item in the collection and sets the UseNtlmForClientToProxyAuth property to False. 
  
```
Get-CsProxyConfiguration -Filter service:* | Set-CsProxyConfiguration -UseNtlmForClientToProxyAuth $False
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Lync Server, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope.
  
The **Set-CsProxyConfiguration** cmdlet provides a way for you to modify the property values of an existing collection of proxy server configuration settings. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsProxyConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsProxyConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AcceptClientCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the proxy server will accept all incoming compression requests from client endpoints.  <br/> |
| _AcceptServerCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the proxy server will accept all incoming compression requests from other servers.  <br/> |
| _AllowPartnerPollingSubscribes_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set the True, partner applications are allowed to periodically poll the service for state changes. The default value is False ($False).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisableNtlmFor2010AndLaterClients_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users logging on from Lync must use the Kerberos protocol for authentication. The default value is False.  <br/> |
| _DnsCacheRecordCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of records that can be maintained in the DNS record cache. The default value is 30000.  <br/> |
| _EnableLoggingAllMessageBodies_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Lync Server will log the actual content of all instant messages. For privacy reasons, message content is typically deleted and only information about the communicating endpoints is included in the log files.  <br/> The default value is False.  <br/> |
| _EnableWhiteSpaceKeepAlive_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) the proxy server expects clients to periodically send a "whitespace message" (an empty message with no content) to indicate that the connection is still active.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the proxy server configuration settings to be modified. To modify the global settings, use this syntax: -Identity global. To modify settings configured at the service scope, use syntax similar to this: -Identity "service: EdgeServer:atl-edge-001.litwareinc.com".  <br/> If this parameter is not included, the **Set-CsProxyConfiguration** cmdlet will automatically modify the global settings.  <br/> |
| _Instance_ <br/> |Optional  <br/> |ProxySettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _LoadBalanceEdgeServers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When True, software load balancing is employed for requests to Edge Servers. The default value is True ($True).  <br/> |
| _LoadBalanceInternalServers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When True, software load balancing is employed for requests to Registrars and other internal servers. The default value is true ($True).  <br/> |
| _MaxClientCompressionCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of client-to-server connections that can be compressed at any given time; additional connections beyond this limit will not be compressed. The compression count can be set to any integer value between 0 and 65535, inclusive. The default value is 15000.  <br/> |
| _MaxClientMessageBodySizeKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum-allowed size (in kilobytes) for the body of a message sent from a client endpoint. The default value is 128, meaning that messages with a body size larger than 128 KB will be rejected. The client message body size can be set to any integer value between 64 and 256, inclusive.  <br/> |
| _MaxKeepAliveInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the amount of time (in minutes) that can elapse before the server verifies that the connection with the client is still valid. The default value is 20 minutes.  <br/> |
| _MaxServerCompressionCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of server-to-server connections that can be compressed at any given time; additional connections beyond this limit will not be compressed. The server compression count can be set to any integer value between 0 and 65535, inclusive. The default value is 1024.  <br/> |
| _MaxServerMessageBodySizeKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum-allowed size (in kilobytes) for the body of a message sent from another server. The default value is 5000, meaning that messages with a body size larger than 5000 KB will be rejected. The server message body size can be set to any integer value between 1000 and 20000, inclusive.  <br/> |
| _OutgoingTlsCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of Transport Layer Security (TLS) connections that can be used for each internal server. The minimum number of TLS connections is 1, and the maximum number is 4. By default, OutgoingTlsCount is set to 4.  <br/> |
| _Realm_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.IRealmChoice  <br/> |Indicates whether or not security credentials are processed by the default proxy server realm (SIP Communication Services) or by a custom realm. Custom realms must be specified (and created) by using the **New-CsSipProxyCustom** cmdlet.  <br/> |
| _RequestServerCompression_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) the proxy server requests that compression be used on all outgoing connections to other servers.  <br/> |
| _TreatAllClientsAsRemote_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the proxy server functions as if all client connections are external connections that pass through the Edge Server. The default value is False.  <br/> |
| _UseCertificateForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use certificates for authentication.  <br/> |
| _UseKerberosForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use the Kerberos protocol for authentication. Although Kerberos is a more secure protocol than NTLM, it cannot be used if the client belongs to a different realm than the server.  <br/> |
| _UseNtlmForClientToProxyAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), client endpoints will be allowed to use the NTLM protocol for authentication. Although NTLM is a less secure protocol than Kerberos, NTLM can be used if the client belongs to a different domain than the server. That is not the case with Kerberos authentication.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object. The **Set-CsProxyConfiguration** cmdlet accepts pipelined instances of the proxy settings object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsProxyConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)
  
[New-CsProxyConfiguration](new-csproxyconfiguration.md)
  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

