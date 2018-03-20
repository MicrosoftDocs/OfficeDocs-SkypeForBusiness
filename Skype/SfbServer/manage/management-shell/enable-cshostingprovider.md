---
title: "Enable-CsHostingProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0ba76785-6c6d-4ee6-9418-5c77b2cbaedf
description: "Enables a hosting provider for use in your organization. A hosting provider is a third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010."
---

# Enable-CsHostingProvider
 
Enables a hosting provider for use in your organization. A hosting provider is a third-party organization that provides instant messaging, presence, and related services for a domain that you would like to federate with. Hosting providers differ from public providers (such as Yahoo!, MSN, and AOL) in that their services are not offered to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Enable-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, the hosting provider with the Identity Fabrikam.com is enabled for use. Note that this command will return an error if Fabrikam.com has already been enabled for use.
  
```
Enable-CsHostingProvider -Identity Fabrikam.com
```

### EXAMPLE 2

Example 2 shows how you can enable all the hosting providers that are currently disabled. To do this, the command first calls the **Get-CsHostingProvider** cmdlet without any additional parameters in order to return a collection of all the hosting providers currently configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects any provider where the Enabled property is equal to False; by definition, that is any provider that is currently disabled. This filtered collection is then piped to the **Enable-CsHostingProvider** cmdlet, which enables each of the providers in the collection.
  
```
Get-CsHostingProvider | Where-Object {$_.Enabled -eq $False} | Enable-CsHostingProvider
```

### EXAMPLE 3

In Example 3, all of the hosting providers used in a "split domain" setup are enabled for use. (Split domain means that some of your Skype for Business Server 2015 accounts are maintained on-premises while other accounts are maintained by a hosting provider.) To carry out this task, the command first uses the **Get-CsHostingProvider** cmdlet to return a collection of all the currently-configured hosting providers. This collection is then piped to the **Where-Object** cmdlet, which selects only those providers that meet two criteria: 1) the EnabledSharedAddressSpace property is equal to True; and, 2) the Enabled property is equal to False. After that, the filtered collection is piped to the **Enable-CsHostingProvider** cmdlet, which enables each provider in the collection.
  
```
Get-CsHostingProvider | Where-Object {$_.EnabledSharedAddressSpace -eq $True -and $_.Enabled -eq $False} | Enable-CsHostingProvider
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A hosting provider is an organization which provides SIP communication services for other organizations; for example, Fabrikam, Inc. might host users from Contoso, Northwind Traders and Wingtip Toys. When you establish a federation relationship with a hosting provider, you effectively establish federation with any organization hosted by that provider. For example, if you federate with Fabrikam, your users will be able to exchange instant messages and presence information with users from Contoso, Northwind Traders, and Wingtip Toys.
  
Hosting providers are also used in split domain scenarios. In a split domain scenario, some of your Skype for Business Server 2015 users have accounts hosted on-premises (that is, hosted on your local implementation of Skype for Business Server 2015). Other users have their accounts maintained off-premises by the third-party hosting provider. Federating with the hosting provider enables on-premises and off-premises users to communicate with one another.
  
In order to federate with a third-party hosting provider, you need to create and enable a new hosting provider. (In addition, the third-party provider will need to create a federation relationship with you.) You can enable a hosting provider at the time that provider is created; alternatively, you can enable that provider after-the-fact by using the **Enable-CsHostingProvider** cmdlet
  
Note that you cannot federate with a hosting provider if your Edge Servers are configured to use default routing rather than Domain Name System (DNS) server routing. 
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the hosting provider to be enabled. The Identity is might be the fully qualified domain name (FQDN) of the hosting provider (for example, fabrikam.com) or perhaps the name of the company providing the services (Fabrikam, Inc.).  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayHostingProvider object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object. The **Enable-CsHostingProvider** cmdlet accepts pipelined instances of the hosting provider object.
  
## Return Types

None. Instead, the cmdlet enables instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider object.
  
## See also

#### 

[Disable-CsHostingProvider](disable-cshostingprovider.md)
  
[Get-CsHostingProvider](get-cshostingprovider.md)
  
[New-CsHostingProvider](new-cshostingprovider.md)
  
[Remove-CsHostingProvider](remove-cshostingprovider.md)
  
[Set-CsHostingProvider](set-cshostingprovider.md)

