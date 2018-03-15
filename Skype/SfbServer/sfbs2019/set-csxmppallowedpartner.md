---
title: "Set-CsXmppAllowedPartner"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 12586746-fbea-44b1-b656-a98028c90552
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsXmppAllowedPartner
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies an existing XMPP allowed partner. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users are allowed to exchange instant messages and presence information with your Lync Server 2013 users. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsXmppAllowedPartner [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 disables dialback negotiation for the XMPP allowed partner contoso.com. This is done by including the SupportDialbackNegotiation parameter and setting the parameter value to False ($False).
  
```
Set-CsXmppAllowedPartner -Identity "contoso.com" -SupportDialbackNegotiation $False
```

### Example 2

In the preceding example, Simple Authentication and Security Layer negotiation is enabled (and required) for all the XMPP allowed partners in the organization. To carry out this task, the command first uses the **Get-CsXmppAllowedPartner** cmdlet to return a collection of all the XMPP allowed partners. That collection is then piped to the **Set-CsXmppAllowedPartner** cmdlet, which sets the value of the SaslNegotiation property for each partner in the collection to Required. 
  
```
Get-CsXmppAllowedPartner | Set-CsXmppAllowedPartner -SaslNegotiation "Required"
```

### Example 3

In Example 3, a new child domain - na.contoso.com - is added to the XMPP allowed partner contoso.com. To do this, the AdditionalDomains parameter is included, along with the syntax @{Add="na.contoso.com"}. That syntax adds na.contoso.com to any other domains currently found in the AdditionalDomains property.
  
```
Set-CsXmppAllowedPartner -Identity "contoso.com" -AdditionalDomains @{Add="na.contoso.com"}
```

### Example 4

Example 4 removes the domain europe.contoso.com from the collection of additional domains assigned to the XMPP allowed partner contoso.com. To remove this domain, the AdditionalDomains parameter is included along with the parameter value @{Remove="europe.contoso.com"}. That syntax removes Europe.contoso.com from the AdditionalDomains property without affecting any other domains that might also be stored in AdditionalDomains.
  
```
Set-CsXmppAllowedPartner -Identity "contoso.com" -AdditionalDomains @{Remove="europe.contoso.com"}
```

### Example 5

The command shown in Example 5 removes child domain support for the XMPP allowed partner contoso.com. This is done by including the AdditionalDomains parameter and the parameter value $Null; that deletes any domains currently included in the AdditionalDomains property.
  
```
Set-CsXmppAllowedPartner -Identity "contoso.com" -AdditionalDomains $Null
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.
  
In order for your users to be able to exchange instant messages and presence information with users on an XMPP network, that network must be configured as an XMPP allowed partner. (You must also assign your users an external access policy that allows XMPP access.) By design, your users will be allowed to communicate with users on any XMPP network that is listed on the allowed partners list. If you do not want users communicating with users from a given network then you must delete that network from the allowed partners list.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsXmppAllowedPartner"}
  
 **Lync Server Control Panel:** To edit the property values for an existing XMPP allowed partner using the Lync Server Control Panel, click External User Access, click XMPP Federated Partners, and then double-click the partner to be modified. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AdditionalDomains_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Additional XMPP domains belonging to the allowed partner.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ConnectionLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of simultaneous connections to a specific partner.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text regarding the XMPP allowed partner. For example, the Description might include contact information for the partner.  <br/> |
| _EnableKeepAlive_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not the XMPP partner should periodically transmit "keep alive" packets in order to verify that the connection is still active.The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the XMPP allowed partner to be modified (for example, fabrikam.com).  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PartnerType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.PartnerType  <br/> |Specifies the relationship between Lync Server 2013 and the XMPP partner. Allowed values are:  <br/> \* Federated (the XMPP partner is from a federated domain)  <br/> \* PublicVerified  <br/> \* PublicUnverified  <br/> The default value is PublicUnverified.  <br/> |
| _ProxyFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Full qualified domain name of the proxy server used by the XMPP partner.  <br/> |
| _SaslNegotiation_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.SaslNegotiation  <br/> |Indicates support for the Simple Authentication and Security Layer protocol, a protocol used for server authentication.  <br/> Allowed values are:  <br/> \* Required (SASL negotiation must be supported)  <br/> \* Optional (SASL will be used  <br/> \* NotSupported (SASL negotiation will not be supported) if available)  <br/> The default value is Required.  <br/> |
| _SupportDialbackNegotiation_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether dialback negotiation will be supported. With dialback negotiation, when Server A contacts Server B communication is not immediately established. Instead, Server B first attempts to verify the identity if Server A by contacting the authoritative DNS server for the domain that Server A claims to be from.  <br/> Note that dialback negotiation is not as secure as SASL or TLS. Instead, it is primarily used in situations where certificates cannot be used to verify a server's identity.  <br/> The default value is True.  <br/> |
| _TlsNegotiation_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.TlsNegotiation  <br/> |Indicates support for the Transport Layer Security protocol, a protocol used to encrypt server-to-server data streams.  <br/> Allowed values are:  <br/> \* Required (TLS negotiation must be supported)  <br/> \* Optional (TLS will be used if available)  <br/> \* NotSupported (TLS negotiation will not be supported)  <br/> The default value is Required.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsXmppAllowedPartner** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsXmppAllowedPartner** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)
  
[New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)
  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)

