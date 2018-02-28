---
title: "Enable-CsPublicProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 98370dfd-9a53-41a8-a1f3-bb7a516c3c5e
description: "Enables a public provider configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010."
---

# Enable-CsPublicProvider
[]
Enables a public provider configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Enable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 enables the public provider with the Identity Skype. This command will return an error if Skype is already enabled.
  
```
Enable-CsPublicProvider -Identity "Skype"
```

### EXAMPLE 2

Example 2 enables all the public providers that are currently disabled. In order to carry out this task, the command first uses the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. That collection is piped to the **Where-Object** cmdlet, which selects only those providers where the Enabled property is equal to False. The filtered collection is then piped to the **Enable-CsPublicProvider** cmdlet, which enables each provider in the collection.
  
```
Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Enable-CsPublicProvider
```

### EXAMPLE 3

Example 3 enables all the public providers that are not currently enabled, provided the verification level of those providers is set to AlwaysVerifiable. To do this, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which picks out those providers that meet two criteria: 1) the VerificationLevel property is equal to AlwaysVerifiable; and, 2) the Enabled property is equal to False. (The -and operator tells the **Where-Object** cmdlet that objects must meet all the specified criteria in order to be selected.) This filtered collection is then piped to the **Enable-CsPublicProvider** cmdlet, which enables each provider in the collection.
  
```
Get-CsPublicProvider | Where-Object {$_.VerificationLevel -eq "AlwaysVerifiable" -and $_.Enabled -eq $False} | Enable-CsPublicProvider
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Skype your users will be able to exchange instant messages and presence information with anyone who has a Skype instant messaging account.
  
In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) Public providers can be enabled at the time they are created, or they can be enabled after-the-fact by using the **Enable-CsPublicProvider** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the public provider to be enabled. The Identity is typically the name of the website providing the services (for example, Yahoo!; AOL; and MSN).  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayPublicProvider object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object. The **Enable-CsPublicProvider** cmdlet accepts pipelined instances of the public provider object.
  
## Return Types

None. Instead, the cmdlet enables instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.
  
## See also

#### 

[Disable-CsPublicProvider](disable-cspublicprovider.md)
  
[Get-CsPublicProvider](get-cspublicprovider.md)
  
[New-CsPublicProvider](new-cspublicprovider.md)
  
[Remove-CsPublicProvider](remove-cspublicprovider.md)
  
[Set-CsPublicProvider](set-cspublicprovider.md)

