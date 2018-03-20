---
title: "New-CsXmppAllowedPartner"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 02f8525a-d8ec-49d8-805b-e76c5449c553
description: "Creates a new XMPP allowed partner. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users have been authorized to exchange instant messages and presence information with your Skype for Business Server 2015 users. This cmdlet was introduced in Lync Server 2013."
---

# New-CsXmppAllowedPartner
 
Creates a new XMPP allowed partner. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users have been authorized to exchange instant messages and presence information with your Skype for Business Server 2015 users. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsXmppAllowedPartner -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new XMPP allowed partner: contoso.com. In this example, the PartnerType property is set to "PublicVerified".
  
```
New-CsXmppAllowedPartner -Identity "contoso.com" -PartnerType "PublicVerified"
```

### Example 2

Example 2 creates a new XMPP allowed partner with the Identity fabrikam.com. In addition to the root domain (fabrikam.com), the AdditionalDomains property is included to allow support for the child domain research.fabrikam2.com.
  
```
New-CsXmppAllowedPartner -Identity "fabrikam.com" -AdditionalDomains "research.fabrikam2.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.
  
In order for your users to be able to exchange instant messages and presence information with users on an XMPP network, that network must be configured as an XMPP allowed partner. (You must also assign your users an external access policy that allows XMPP access.) By design, your users will be allowed to communicate with users on any XMPP network that is listed on the allowed partners list. If you do not want users communicating with users from a given network then you must delete that network from the allowed partners list.
  
 **Skype for Business Server Control Panel:** To create a new XMPP allowed partner using Skype for Business Server Control Panel, click External User Access, click XMPP Federated Partners, and then click New.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Required  <br/> |System.String  <br/> |Primary domain of the XMPP allowed partner; for example:  <br/>  `-Domain "fabrikam.com"` <br/> You can specify the primary domain by using either the Domain parameter or the Identity parameter. However, you cannot use both parameters in the same command.  <br/> Additional domains can be specified by using the AdditionalDomains parameter.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Primary domain of the XMPP allowed partner; for example:  <br/>  `-Identity "fabrikam.com"` <br/> You can specify the primary domain by using either the Identity parameter or the Domain parameter. However, you cannot use both parameters in the same command.  <br/> Additional domains can be specified by using the AdditionalDomains parameter.  <br/> |
| _AdditionalDomains_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Additional XMPP domains belonging to the allowed partner. Multiple domains can be specified by separated domain names by using commas; for example:  <br/>  `-AdditionalDomains "fabrikam2.com","fabrikam3.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ConnectionLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of simultaneous connections allowed to a specific partner.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text regarding the XMPP allowed partner. For example, the Description might include contact information for the partner.  <br/> |
| _EnableKeepAlive_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not the XMPP partner should periodically transmit "keep alive" packets in order to verify that the connection is still active.  <br/> The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _PartnerType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.PartnerType  <br/> |Specifies the relationship between Skype for Business Server 2015 and the XMPP partner. Allowed values are:  <br/> Federated (the XMPP partner is from a federated domain)  <br/> PublicVerified  <br/> PublicUnverified  <br/> The default value is PublicUnverified.  <br/> |
| _ProxyFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Full qualified domain name of the proxy server used by the XMPP partner.  <br/> |
| _SaslNegotiation_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.SaslNegotiation  <br/> |Indicates support for the Simple Authentication and Security Layer protocol, a protocol used for server authentication.  <br/> Allowed values are:  <br/> Required (SASL negotiation must be supported)  <br/> Optional (SASL will be used if available)  <br/> NotSupported (SASL negotiation will not be supported)  <br/> The default value is Required.  <br/> |
| _SupportDialbackNegotiation_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether dialback negotiation will be supported. With dialback negotiation, when Server A contacts Server B communication is not immediately established. Instead, Server B first attempts to verify the identity of Server A by contacting the authoritative DNS server for the domain that Server A claims to be from.  <br/> Note that dialback negotiation is not as secure as SASL or TLS. Instead, it is primarily used in situations where certificates cannot be used to verify a server's identity.  <br/> The default value is True.  <br/> |
| _TlsNegotiation_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.TlsNegotiation  <br/> |Indicates support for the Transport Layer Security protocol, a protocol used to encrypt server-to-server data streams.  <br/> Allowed values are:  <br/> Required (TLS negotiation must be supported)  <br/> Optional (TLS will be used if available)  <br/> NotSupported (TLS negotiation will not be support The default value is Required.)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsXmppAllowedPartner** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsXmppAllowedPartner** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)
  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)
  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

