---
title: "New-CsHostingProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6874cc14-d250-43d4-8868-43cd8d202e9c
description: "Creates a new hosting provider for use in your organization. A hosting provider is a private third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010."
---

# New-CsHostingProvider
 
Creates a new hosting provider for use in your organization. A hosting provider is a private third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsHostingProvider -Enabled <$true | $false> -Identity <XdsGlobalRelativeIdentity> -ProxyFqdn <String> [-AutodiscoverUrl <String>] [-IsLocal <$true | $false>] [-SipClientPort <UInt64>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, a new hosting provider with the Identity Fabrikam.com is created. In addition to specifying the Identity, the command also includes the other two required parameters: ProxyFqdn (which specifies the proxy server used by Fabrikam.com); and Enabled, which indicates whether or not the new hosting provider is enabled for use. If you leave out any of the required parameters, the **New-CsHostingProvider** cmdlet will prompt you to enter those values before continuing.
  
```
New-CsHostingProvider -Identity Fabrikam.com -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True
```

### EXAMPLE 2

Example 2 demonstrates how you can create a new hosting provider for use in a split domain scenario. (Split domain means that some of your Skype for Business Server 2015 accounts are maintained on-premises while other accounts are maintained by a hosting provider.) To create this type of hosting provider, you must include the three required parameters (Identity; ProxyFqdn; and Enabled). In addition, you must include, and set to True, both the HostsOCSUsers and the EnabledSharedAddressSpace parameters. To create a split domain provider that hosts non-Skype for Business Server 2015 services (such as Microsoft Exchange), include these same two parameters but set HostsOCSUsers to False.
  
```
New-CsHostingProvider -Identity Fabrikam.com -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True -HostsOCSUsers $True -EnabledSharedAddressSpace $True
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A hosting provider is an organization which provides SIP communication services for other organizations; for example, Fabrikam, Inc. might host users from Contoso, Northwind Traders, and Wingtip Toys. When you establish a federation relationship with a hosting provider, you effectively establish federation with any organization hosted by that provider. For example, if you federate with Fabrikam, your users will be able to exchange instant messages and presence information with users from Contoso, Northwind Traders, and Wingtip Toys.
  
Hosting providers are also used in split domain scenarios. In a split domain scenario, some of your Skype for Business Server 2015 users have accounts hosted on-premises (that is, hosted on your local implementation of Skype for Business Server 2015). Other users have their accounts maintained off-premises by the third-party hosting provider. Federating with the hosting provider enables on-premises and off-premises users to communicate with one another.
  
In order to federate with a third-party hosting provider, you need to create and enable a new hosting provider. (In addition, the third-party provider will need to create a federation relationship with you.) The **New-CsHostingProvider** cmdlet enables you to set up three types of hosting provider relationships:
  
Direct federation with the hosting provider. To create this type of relationship you must include the three required parameters: Identity; ProxyFqdn; and Enabled.
  
Split domain, with Skype for Business Server 2015 services being hosted. To create this type of relationship you need to include the three required parameters. In addition, you must set both the EnabledSharedAddressSpace and HostsOCSUsers properties to True. 
  
Split domain, with non-Skype for Business Server 2015 services (such as Microsoft Exchange) being hosted. To create this type of relationship, you need to include the three required parameters. In addition, you must set the EnabledSharedAddressSpace to True and HostsOCSUsers to False.
  
When you create a new hosting provider, both the Identity and the proxy fully qualified domain name (FQDN) for that provider must be unique: you cannot have two hosting providers (or even one hosting provider and one public provider) that share an identity and/or a proxy FQDN.
  
Note, too that you cannot federate with a hosting provider if your Edge Servers are configured to use default routing rather than Domain Name System (DNS) server routing. 
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Enabled_ <br/> |Required  <br/> |System.Boolean  <br/> |Indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to True. The default value is False.  <br/> |
| _EnabledSharedAddressSpace_ <br/> |Required  <br/> |System.Boolean  <br/> |If True, indicates that the hosting provider is being used in a split domain scenario. The default value is False.  <br/> |
| _HostsOCSUsers_ <br/> |Required  <br/> |System.Boolean  <br/> |If True, indicates that the hosting provider is used to host Skype for Business Server 2015 accounts. If False, that indicates that the provider hosts other account types, such as Microsoft Exchange accounts. The default value is False.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the hosting provider to be created. The Identity is a string value; the Identity might be the FQDN of the hosting provider (for example, fabrikam.com) or perhaps the name of the company providing the services (Fabrikam, Inc.).  <br/> Hosting provider Identities must be unique. Your command will fail if you try to create a new hosting provider with the same Identity as an existing provider.  <br/> |
| _ProxyFqdn_ <br/> |Required  <br/> |System.String  <br/> |The FQDN for the proxy server used by the hosting provider. Note that this value cannot be modified. If the hosting provider later changes its proxy server or if you make a mistake when you first specify the proxy FQDN you will need to delete and then recreate the entry for that provider.  <br/> |
| _AutodiscoverUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the autodiscover service used by a hosting provider that hosts Skype for Business Server 2015 accounts. The autodiscover service enables client applications to determine how to access resources such as a user's home pool.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _IsLocal_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, indicates that the proxy server used by the hosting provider is contained within your Skype for Business Server 2015 topology. The default value is False.  <br/> |
| _SipClientPort_ <br/> |Optional  <br/> |System.UInt64  <br/> |Port used by the provider for communicating with SIP clients; the default value is 443. Note that, by default, the SipClientPort is not displayed when you run the **Get-CsHostingProvider** cmdlet. To see the SipClientPort, use a command similar to this: <br/>  `Get-CsHostingProvider | Select-Object *` <br/> |
| _VerificationLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType  <br/> |Indicates the allowed verification level for messages sent to and from the hosted provider. The VerificationLevel must be set to one of the following values:  <br/> AlwaysVerifiable. Indicates that all messages sent from the hosting provider are considered verifiable. That means that no messages from the hosting provider will be rejected.  <br/> AlwaysUnverifiable. Indicates that all messages sent from the hosting provider are considered unverifiable. As a result, messages are passed only if the user on the hosting provider is also in your Contacts list.  <br/> UseSourceVerification. Relies on the verification level included in messages sent from the hosting provider. If this level is not specified, then the message will be rejected as being unverifiable.  <br/> The default value is AlwayVerifiable.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsHostingProvider** cmdlet does not accept pipelined input.
  
## Return Types

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object.
  
## See also

#### 

[Disable-CsHostingProvider](disable-cshostingprovider.md)
  
[Enable-CsHostingProvider](enable-cshostingprovider.md)
  
[Get-CsHostingProvider](get-cshostingprovider.md)
  
[Remove-CsHostingProvider](remove-cshostingprovider.md)
  
[Set-CsHostingProvider](set-cshostingprovider.md)

