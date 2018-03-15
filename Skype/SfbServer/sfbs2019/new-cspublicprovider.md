---
title: "New-CsPublicProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0b2dcb40-13f8-4ce6-b537-527d34895ceb
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsPublicProvider
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a federation relationship with a new public provider. A public provider is an organization that provides instant messaging, presence, and related services to the general public. Lync Server ships with three public providers configured but not enabled: Yahoo; AIM (AOL); and Messenger (MSN). This cmdlet was introduced in Lync Server 2010.
  
```
New-CsPublicProvider -Identity <XdsGlobalRelativeIdentity> -Enabled <$true | $false> -ProxyFqdn <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IconUrl <String>] [-InMemory <SwitchParameter>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new federation relationship with a public provider that has the Identity Fabrikam. In addition to specifying the Identity, two other property values (and their corresponding parameters) must be set: ProxyFqdn (set to proxyserver.fabrikam.com) and Enabled (which, in this case, is set to True).
  
```
New-CsPublicProvider -Identity "Fabrikam" -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True
```

### EXAMPLE 2

Example 2 demonstrates how you can create a new public provider in memory only, modify the properties of that provider, then turn the virtual provider into a real provider that can be used in your organization. To do this, the first command in the example creates a public provider with the Identity Fabrikam. In addition to including the required parameters (Identity, ProxyFqdn, and Enabled), the command adds the InMemory parameter; this creates an in-memory-only instance of the provider that is then stored in a variable named $x. 
  
After the in-memory instance of the provider has been created the second command in the example modifies the VerificationLevel of the virtual provider. The final command then uses the **Set-CsPublicProvider** cmdlet to turn the virtual provider (stored in $x) into an actual public provider. If you do not call the **Set-CsPublicProvider** cmdlet the real provider will not be created. In turn, the virtual provider will disappear the moment you end your Windows PowerShell session or delete the variable $x. 
  
```
$x = New-CsPublicProvider -Identity "Fabrikam" -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True -InMemory
$x.VerificationLevel = "AlwaysUnverifiable"
Set-CsPublicProvider -Instance $x
```

## Detailed Description
<a name="sectionSection1"> </a>

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When a federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Lync 2013. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Messenger (MSN), then your users will be able to exchange instant messages and presence information with anyone who has a Messenger instant messaging account.
  
In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) The **Set-CsPublicProvider** enables you to modify property values for any of the public providers that have been configured for use in your organization. 
  
Note that you cannot federate with a public provider if your Edge servers are configured to use default routing rather than DNS server routing. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsPublicProvider** cmdlet: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsPublicProvider"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Enabled_ <br/> |Required  <br/> |System.Boolean  <br/> |Indicates whether or not the federation relationship between your organization and the public provider is active. If set to True, users in your organization will be able to exchange instant messages and presence information with users who have accounts hosted on the public provider. If set to False, users in your organization will not be able to exchange instant messages and presence information with users who have accounts hosted on the public provider. You can enable and disable federation relationships at any time by using the **Enable-CsPublicProvider** cmdlet and the **Disable-CsPublicProvider** cmdlet, respectively.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the public provider to be created. The Identity typically the name of the website providing the services (for example, Yahoo!, AOL, or MSN.).  <br/> Identities must be unique not only among public providers, but also among hosting providers. Suppose you try to create a new public provider with the Identity Fabrikam. Your command will fail if a public provider or a hosting provider with that Identity already exists.  <br/> |
| _ProxyFqdn_ <br/> |Required  <br/> |System.String  <br/> |Specifies the fully qualified domain name (FQDN) (for example, proxyserver.fabrikam.com) of the proxy server used by the public provider.  <br/> Proxy FQDNs must be unique not only among public providers, but also among hosting providers. For example, suppose you try to create a new public provider with the proxy FQDN proxyserver.fabrikam.com. This command will fail if a public provider or a hosting provider with that proxy FQDN already exists.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _IconUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the icon used to indicate a Microsoft Skype contact.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _VerificationLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType  <br/> |Indicates how (or if) messages sent from a public provider are verified to ensure that they were sent from that provider. The VerificationLevel must be set to one of the following values:  <br/> AlwaysVerifiable. All messages purportedly sent from this provider will be accepted. If a verification header is not found in the message it will be added by Lync Server. This is the default value.  <br/> AlwaysUnverifiable. All messages purportedly sent from a public provider are considered unverified. They will be delivered only if they were sent from a person who is on the recipient's Contacts list. For example, if Ken Myer is on your Contacts list you will be able to receive messages from him. If Pilar Ackerman is not on your Contacts list then you will not be able to receive messages from her. Note that Lync 2013 users can manually override this setting, thereby allowing themselves to receive messages people not on their Contacts list.  <br/> UseSourceVerification. Uses the verification header added to the message by the public provider. If the verification information is missing the message will be rejected. This value has been deprecated for use in Lync Server 2013.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsPublicProvider** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Disable-CsPublicProvider](disable-cspublicprovider.md)
  
[Enable-CsPublicProvider](enable-cspublicprovider.md)
  
[Get-CsPublicProvider](get-cspublicprovider.md)
  
[Remove-CsPublicProvider](remove-cspublicprovider.md)
  
[Set-CsPublicProvider](set-cspublicprovider.md)

