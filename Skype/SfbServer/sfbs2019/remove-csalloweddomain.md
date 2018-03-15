---
title: "Remove-CsAllowedDomain"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d38afb34-627e-4772-990c-4f6676c54000
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsAllowedDomain
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a domain from the list of domains approved for federation. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsAllowedDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 removes the domain fabrikam.com from the list of allowed domains. 
  
```
Remove-CsAllowedDomain -Identity fabrikam.com
```

### EXAMPLE 2

In Example 2, all of the domains that have the string value "fabrikam" somewhere in their Identity are removed from the list of allowed domains. To do this, the command first uses the **Get-CsAllowedDomain** cmdlet and the Filter parameter to return a collection of domains that have the string value "fabrikam" somewhere in their Identity (the Identity is the only property you can filter for). That filtered collection is then piped to the **Remove-CsAllowedDomain** cmdlet, which, in turn, removes all of the items in the filtered collection from the list of allowed domains. 
  
```
Get-CsAllowedDomain -Filter *fabrikam* | Remove-CsAllowedDomain
```

### EXAMPLE 3

Example 3 removes all the domains without an identified proxy server from the list of allowed domains. To carry out this task, the **Get-CsAllowedDomain** cmdlet is called to return a collection of all the domains currently on the allowed list. That collection is piped to the **Where-Object** cmdlet, which picks out only those domains where the ProxyFqdn property is equal to a null value. The filtered collection is then piped to the **Remove-CsAllowedDomain** cmdlet, which removes each domain in the collection from the allowed list. 
  
```
Get-CsAllowedDomain | Where-Object {$_.ProxyFqdn -eq $Null} | Remove-CsAllowedDomain 
```

### EXAMPLE 4

In Example 4, all of the domains where the Comment field contains the string value "Ken Myer" are removed from the list of allowed domains. To do this, the command first uses the **Get-CsAllowedDomain** cmdlet to retrieve a collection of all the domains currently on the allowed domains list. This collection is then piped to the **Where-Object** cmdlet, which selects only those domains where the Comment property contains the string value "Ken Myer". This filtered collection is then piped to the **Remove-CsAllowedDomain** cmdlet, which removes each item in the collection from the list of allowed domains. 
  
```
Get-CsAllowedDomain | Where-Object {$_.Comment -match "Ken Myer"} | Remove-CsAllowedDomain 
```

## Detailed Description
<a name="sectionSection1"> </a>

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another by using SIP applications such as Lync. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
Setting up direct federation with another organization involves several tasks. To begin with, you must enable your servers running the Lync Server Access Edge service to allow federation. In addition, the other organization must enable federation with you; federation cannot be established unless both parties agree to the relationship.
  
To set up a federated relationship you might also need to manage two federation-related lists: the allowed list and the blocked list. The allowed list represents the organizations you have chosen to federate with. If a domain appears on the allowed list then (depending on your configuration settings) your users will be able to exchange instant messages and presence information with users who have accounts in that federated domain. Conversely, the blocked list represents domains that users are expressly forbidden from federating with; for example, messages sent from a blocked domain will automatically be rejected by Lync Server.
  
If you want to discontinue a federation relationship, you can use the **Remove-CsAllowedDomain** cmdlet to remove the appropriate domain from the list of allowed domains and then, if appropriate, use the **New-CsBlockedDomain** cmdlet to add the domain to the blocked domain list. Note that a domain cannot simultaneously appear on both the allowed and the blocked lists. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsAllowedDomain** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAllowedDomain"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the domain to be removed from the allowed list; for example, fabrikam.com. You cannot use wildcards when specifying a domain Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain object. The **Remove-CsAllowedDomain** cmdlet accepts pipelined instances of the allowed domain object. 
  
## Return Types
<a name="sectionSection3"> </a>

Deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAllowedDomain](get-csalloweddomain.md)
  
[New-CsAllowedDomain](new-csalloweddomain.md)
  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
  
[Set-CsAllowedDomain](set-csalloweddomain.md)

