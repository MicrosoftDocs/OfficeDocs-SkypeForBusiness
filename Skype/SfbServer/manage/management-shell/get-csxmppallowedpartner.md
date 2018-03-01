---
title: "Get-CsXmppAllowedPartner"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6d031b38-325a-4196-998f-c473390f2055
description: "Returns information about XMPP partners authorized to communicate with your organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. Allowed partners are IM and presence providers that have been authorized to exchange instant messages and presence information with your Skype for Business Server 2015 users. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsXmppAllowedPartner
 
Returns information about XMPP partners authorized to communicate with your organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. Allowed partners are IM and presence providers that have been authorized to exchange instant messages and presence information with your Skype for Business Server 2015 users. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsXmppAllowedPartner [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the XMPP allowed partners configured for use in the organization.
  
```
Get-CsXmppAllowedPartner
```

### Example 2

In Example 2, information is returned for a single XMPP allowed partner: the partner with the Identity xmpp.contoso.com.
  
```
Get-CsXmppAllowedPartner -Identity "xmpp.contoso.com"
```

### Example 3

Example 3 returns information for all the XMPP allowed partners that have an Identity that ends in the string value ".org" (for example, xmpp.contoso.org and xmpp.fabrikam.org).
  
```
Get-CsXmppAllowedPartner - Filter "*.org"
```

### Example 4

The command shown in Example 4 returns information about all the XMPP allowed partners where Simple Authentication and Security Layer negotiation is required. In order to do this, the command first uses the **Get-CsXmppAllowedPartner** cmdlet to return information about all the allowed XMPP allowed partners. The returned partners are then piped to the **Where-Object** cmdlet, which selects only those partners where the SaslNegotiation property is equal to Required.
  
```
Get-CsXmppAllowedPartner | Where-Object {$_.SaslNegotiation -eq "Required"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.
  
In order for your users to be able to exchange instant messages and presence information with users on an XMPP network, that network must be configured as an XMPP allowed partner. (You must also assign your users an external access policy that allows XMPP access.) By design, your users will be allowed to communicate with users on any XMPP network that is listed on the allowed partners list. If you do not want users communicating with users from a given network then you must delete that network from the allowed partners list.
  
 **Skype for Business Server Control Panel:** To view information about your XMPP allowed partners in the Skype for Business Server Control Panel, click External User Access and then click XMPP Federated Partners.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identities of the XMPP allowed partner (or partners) to be returned. For example the filter value "\*.org" returns a collection of all the XMPP allowed partners that have an Identity that ends with the string value ".org".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the XMPP allowed partner to be returned (for example, fabrikam.com). If neither this parameter nor the Filter parameter is specified, then all the XMPP partners configured for use in your organization are returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the XMPP allowed partner data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsXmppAllowedPartner** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsXmppAllowedPartner** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)
  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)
  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

