---
title: "Disable-CsHostingProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67d67111-aa04-4241-8f41-e8059fd1649c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Disable-CsHostingProvider
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Disables a hosting provider currently in use in your organization. A hosting provider is a third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers, such as Microsoft Lync Online 2010, differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Disable-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 disables the hosting provider Fabrikam.com. Note that this command will return an error message if Fabrikam.com is already disabled.
  
```
Disable-CsHostingProvider -Identity "Fabrikam.com"
```

### EXAMPLE 2

Example 2 disables all the hosting providers that are currently enabled. To do this, the command first calls the **Get-CsHostingProvider** cmdlet to return a collection of all the hosting providers configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those providers where the Enabled property is equal to True. The filtered collection is then piped to the **Disable-CsHostingProvider** cmdlet, which disables each provider in the collection. 
  
```
Get-CsHostingProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsHostingProvider
```

### EXAMPLE 3

In Example 3, all the enabled hosting providers where the verification level is not equal to AlwaysVerifiable are disabled. To carry out this task, the command first uses the **Get-CsHostingProvider** cmdlet to return a collection of all the hosting providers configured for use in the organization. This collection is piped to the **Where-Object** cmdlet, which selects only those providers that meet two criteria: 1) the VerificationLevel property is not equal to AlwaysVerifiable; and, 2) the Enabled property is equal to True. The filtered collection is then piped to the **Disable-CsHostingProvider** cmdlet, which disables each provider in the collection. 
  
```
Get-CsHostingProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsHostingProvider
```

## Detailed Description
<a name="sectionSection1"> </a>

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Lync 2013. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A hosting provider is an organization that provides SIP communication services for other organizations; for example, Fabrikam, Inc. might host users from Contoso, Northwind Traders, and Wingtip Toys. When you establish a federation relationship with a hosting provider, you effectively establish federation with any organization hosted by that provider. For example, if you federate with Fabrikam, your users will be able to exchange instant messages and presence information with users from Contoso, Northwind Traders, and Wingtip Toys.
  
Hosting providers are also used in split domain scenarios. In a split domain scenario, some of your Lync Server users have accounts hosted on-premises (that is, hosted on your local implementation of Lync Server). Other users have their accounts maintained off-premises by the third-party hosting provider. Federating with the hosting provider enables on-premises and off-premises users to communicate with one another.
  
In order to federate with a third-party hosting provider you need to create and enable a new hosting provider. (In addition, the third-party provider will need to create a federation relationship with you.) You can enable a hosting provider at the time that provider is created; alternatively, you can enable the provider after-the-fact by using the **Enable-CsHostingProvider** cmdlet. In addition, you can use the **Disable-CsHostingProvider** cmdlet to disable the relationship at any time. When you disable a hosting provider that provider remains a valid federation partner; however, all communication activity between your organization and the provider will be suspended until the provider has been re-enabled. 
  
Note that you cannot federate with a hosting provider if your Edge Servers are configured to use default routing rather than Domain Name System (DNS) server routing. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Disable-CsHostingProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Disable-CsHostingProvider"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the hosting provider to be disabled. The Identity might be the fully qualified domain (FQDN) name of the hosting provider (for example, fabrikam.com) or perhaps the name of the company providing the services (Fabrikam, Inc.).  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayHostingProvider object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object. The **Disable-CsHostingProvider** cmdlet accepts pipelined instances of the hosting provider object. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the cmdlet disables instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Enable-CsHostingProvider](enable-cshostingprovider.md)
  
[Get-CsHostingProvider](get-cshostingprovider.md)
  
[New-CsHostingProvider](new-cshostingprovider.md)
  
[Remove-CsHostingProvider](remove-cshostingprovider.md)
  
[Set-CsHostingProvider](set-cshostingprovider.md)

