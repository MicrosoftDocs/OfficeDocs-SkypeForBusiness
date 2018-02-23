---
title: "Set-CsHostingProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 709567e3-1af6-4829-b9ce-5f488f9db372
description: "Modifies a hosting provider currently in use in your organization. A hosting provider is a third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsHostingProvider
[]
Modifies a hosting provider currently in use in your organization. A hosting provider is a third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 modifies the hosting provider with the Identity Fabrikam.com. In this example, the VerificationLevel property is set to AlwaysUnverifiable.
  
```
Set-CsHostingProvider -Identity "Fabrikam.com" -VerificationLevel "AlwaysUnverifiable"
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the verification level for all the hosting providers is set to AlwaysUnverifiable. To do this, **Get-CsHostingProvider** is first used to return a collection of all the hosting providers configured for use in the organization. This collection is then piped to **Set-CsHostingProvider**, which modifies the VerificationLevel property for each provider in the collection.
  
```
Get-CsHostingProvider | Set-CsHostingProvider -VerificationLevel "AlwaysUnverifiable"
```

### EXAMPLE 3

In Example 3 all the hosting providers currently configured for use in a split domain setup are modified so that they are no longer used for split domain federation. In this example, **Get-CsHostingProvider** is first called in order to return a collection of all the available hosting providers. This collection is then piped to the **Where-Object** cmdlet, which selects only those providers that meet two criteria: 1) the HostsOCSUsers property is equal to True; and, 2) the EnabledSharedAddressSpace property is equal to True. This filtered collection is then piped to **Set-CsHostingProvider**, which sets both the EnabledSharedAddressSpace and the HostsOCSUsers properties to False. When this is done any hosting providers in the collection will still be enabled for federation; however, they will no longer be used in a split domain scenario.
  
```
Get-CsHostingProvider | Where-Object {$_.EnabledSharedAddressSpace -eq $True -and $_.HostsOCSUsers -eq $True} | Set-CsHostingProvider -EnabledSharedAddressSpace $False -HostsOCSUsers $False
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When a federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A hosting provider is an organization that provides SIP communication services for other organizations; for example, Fabrikam, Inc. might host users from Contoso, Northwind Traders, and Wingtip Toys. When you establish a federation relationship with a hosting provider, you effectively establish federation with any organization hosted by that provider. For example, if you federate with Fabrikam, your users will be able to exchange instant messages and presence information with users from Contoso, Northwind Traders, and Wingtip Toys.
  
Hosting providers are also used in split domain scenarios. In a split domain scenario, some of your Skype for Business Server 2015 users have accounts hosted on-premises (that is, hosted on your local implementation of Skype for Business Server 2015). Other users have their accounts maintained off-premises by the third-party hosting provider. Federating with the hosting provider enables on-premises and off-premises users to communicate with one another.
  
In order to federate with a third-party hosting provider you need to create and enable a new hosting provider. (In addition, the third-party provider will need to create a federation relationship with you.) After a hosting provider has been created, you can use the **Set-CsHostingProvider** cmdlet to modify the properties of that provider. For example, you can use this cmdlet to change the fully qualified domain name (FQDN) of the provider's proxy server, or use the cmdlet to change the verification level for that provider.
  
Note that you cannot federate with a hosting provider if your Edge Servers are configured to use default routing rather than Domain Name System (DNS) server routing. 
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AutodiscoverUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the autodiscover service used by a hosting provider that hosts Skype for Business Server 2015 accounts. The autodiscover service enables client applications such as Microsoft Lync Mobile to determine how to access resources such as a user's home pool.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to True. The default value is False.  <br/> |
| _EnabledSharedAddressSpace_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, indicates that the hosting provider is being used in a split domain scenario. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HostsOCSUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, indicates that the hosting provider is used to host Skype for Business Server 2015 accounts. If False, that indicates that the provider hosts other account types, such as Microsoft Exchange Server accounts. The default value is False.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the hosting provider to be modified. The Identity might be the FQDN of the hosting provider (for example, fabrikam.com) or perhaps the name of the company providing the services (Fabrikam, Inc.).  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayHostingProvider object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _IsLocal_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, indicates that the proxy server used by the hosting provider is contained within your own Skype for Business Server 2015 topology. The default value is False.  <br/> |
| _SipClientPort_ <br/> |Optional  <br/> |System.UInt64  <br/> |Port used by the provider for communicating with SIP clients; the default value is 443. Note that, by default, the SipClientPort is not displayed when you run the Get-CsHostingProvider cmdlet. To see the SipClientPort, use a command similar to this:  <br/>  `Get-CsHostingProvider | Select-Object *` <br/> |
| _VerificationLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType  <br/> |Indicates the allowed verification level for messages sent to and from the hosted provider. The VerificationLevel must be set to one of the following values:  <br/> AlwaysVerifiable. Indicates that all messages sent from the hosting provider are considered verifiable. That means that no messages from the hosting provider will be rejected.  <br/> AlwaysUnverifiable. Indicates that all messages sent from the hosting provider are considered unverifiable. As a result, messages are passed only if the user on the hosting provider is also in your Contacts list.  <br/> UseSourceVerification. Relies on the verification level included in messages sent from the hosting provider. If this level is not specified, then the message will be rejected as being unverifiable.  <br/> The default value is AlwaysVerifiable.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object. **Set-CsHostingProvider** accepts pipelined instances of the hosting provider object.
  
## Return Types

 **Set-CsHostingProvider** does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object.
  
## See also

#### 

[Disable-CsHostingProvider](disable-cshostingprovider.md)
  
[Enable-CsHostingProvider](enable-cshostingprovider.md)
  
[Get-CsHostingProvider](get-cshostingprovider.md)
  
[New-CsHostingProvider](new-cshostingprovider.md)
  
[Remove-CsHostingProvider](remove-cshostingprovider.md)

