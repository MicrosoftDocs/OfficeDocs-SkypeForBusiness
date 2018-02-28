---
title: "Remove-CsPublicProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b9eec2f4-cf36-41b7-8023-67790cc8d4cd
description: "Removes a public provider configured for use in your organization. A public provider is an organization that provides instant messaging (IM), presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsPublicProvider
[]
Removes a public provider configured for use in your organization. A public provider is an organization that provides instant messaging (IM), presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsPublicProvider -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 deletes the public provider with the Identity Skype. After this command has completed, Skype will no longer appear in the list of configured public providers; at that point, the only way to re-establish federation with Skype is to re-create the provider.
  
```
Remove-CsPublicProvider -Identity "Skype"
```

### EXAMPLE 2

Example 2 deletes all the public providers configured for use in the organization. To do this, the command first uses the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently configured for use. This collection is then piped to the **Remove-CsPublicProvider** cmdlet, which, in turn, deletes each provider in the collection.
  
```
Get-CsPublicProvider | Remove-CsPublicProvider
```

### EXAMPLE 3

In Example 3, all the public providers that are currently disabled are removed from the set of configured pubic providers. To carry out this task, the command first uses the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently configured for use. This collection is piped to the **Where-Object** cmdlet, which selects only those providers where the Enabled property is equal to False. That filtered collection is then piped to the **Remove-CsPublicProvider** cmdlet, which deletes all the items in the collection.
  
```
Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Remove-CsPublicProvider
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When a federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Skype your users will be able to exchange instant messages and presence information with anyone who has a Skype instant messaging account.
  
In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) If you decide later on to terminate this relationship, you can use the **Remove-CsPublicProvider** cmdlet to delete the public provider. When you delete a public provider, the provider is removed from your list of federated partners; at that point, the only way to re-establish the relationship is to re-create the provider. If you want to temporarily suspend a relationship, use the **Disable-CsPublicProvider** cmdlet instead. When a public provider is disabled the provider is not deleted from the list of federated partners; instead, the provider is simply marked as disabled and communication between your organization and that provider is suspended. To re-establish the relationship you can use the **Enable-CsPublicProvider** cmdlet to re-enable the provider.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the public provider to be removed. The Identity typically the name of the website providing the services.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object. The **Remove-CsPublicProvider** cmdlet accepts pipelined instances of the public provider object.
  
## Return Types

None. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.
  
## See also

#### 

[Disable-CsPublicProvider](disable-cspublicprovider.md)
  
[Enable-CsPublicProvider](enable-cspublicprovider.md)
  
[Get-CsPublicProvider](get-cspublicprovider.md)
  
[New-CsPublicProvider](new-cspublicprovider.md)
  
[Set-CsPublicProvider](set-cspublicprovider.md)

