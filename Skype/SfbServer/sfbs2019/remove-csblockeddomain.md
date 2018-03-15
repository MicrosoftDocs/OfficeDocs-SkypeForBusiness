---
title: "Remove-CsBlockedDomain"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 34485703-9e1d-47f9-9834-c2ba37249cd1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsBlockedDomain
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a domain from the list of domains that are blocked for federation. By definition, your users are not allowed to use Lync Server applications to communicate with people from the blocked domain; for example, users cannot use Lync to exchange instant messages with anyone with a SIP account in a domain that appears on the blocked list. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsBlockedDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 removes the domain fabrikam.com from the list of blocked domains. This is done by calling the **Remove-CsBlockedDomain** cmdlet and specifying the domain with the Identity "fabrikam.com". 
  
```
Remove-CsBlockedDomain -Identity fabrikam.com
```

### EXAMPLE 2

In Example 2, all the domains that have an Identity that includes the string value "fabrikam" are removed from the list of blocked domains. To do this, the **Get-CsBlockedDomain** cmdlet and the Filter parameter are first used to return a collection of all the blocked domains that include the string "fabrikam" somewhere in their Identity (for example, fabrikam.com, fabrikam.org, or us.fabrikam.net). That collection is then piped to the **Remove-CsBlockedDomain** cmdlet, which deletes each item in the collection from the list of blocked domains. 
  
```
Get-CsBlockedDomain -Filter *fabrikam* | Remove-CsBlockedDomain 
```

### EXAMPLE 3

The command shown in Example 3 completely clears the list of blocked domains. This is done by first calling the **Get-CsBlockedDomain** cmdlet without any parameters; that results in a returned collection that consists of all the domains currently on the blocked domain list. That collection is then piped to the **Remove-CsBlockedDomain** cmdlet, which removes each item in the collection from the blocked domain list. The net result: no domains will be left on the blocked domain list. 
  
```
Get-CsBlockedDomain | Remove-CsBlockedDomain 
```

## Detailed Description
<a name="sectionSection1"> </a>

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another by using SIP applications such as Lync. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
Setting up direct federation with another organization involves several tasks. To begin with, you must enable your servers running the Lync Server Access Edge service to allow federation. In addition, the other organization must enable federation with you; federation cannot be established unless both parties agree to the relationship.
  
To establish a federated relationship you might also need to manage two federation-related lists: the allowed list and the blocked list. The allowed list represents the organizations you have chosen to federate with; if a domain appears on the allowed list then (depending on your configuration settings) your users will be able to exchange instant messages and presence information with users who have accounts in that federated domain. Conversely, the blocked list represents domains that users are expressly forbidden from federating with; for example, messages sent from a blocked domain will automatically be rejected by Lync Server.
  
Of course, messages are rejected only as long as the domain appears on the blocked list; after a domain has been removed from the list you can then establish a federated relationship with that domain. To enable federation with a previously-prohibited domain, you must first use the **Remove-CsBlockedDomain** cmdlet to remove that domain from the list of blocked domains. A domain cannot simultaneously appear on both the allowed and the blocked lists 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsBlockedDomain** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsBlockedDomain"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the domain to be removed from the blocked list; for example, fabrikam.com. Note that you cannot use wildcards when specifying a domain Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain object. The **Remove-CsBlockedDomain** cmdlet accepts pipelined instances of the blocked domain object. 
  
## Return Types
<a name="sectionSection3"> </a>

Deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsBlockedDomain](get-csblockeddomain.md)
  
[New-CsBlockedDomain](new-csblockeddomain.md)
  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
  
[Set-CsBlockedDomain](set-csblockeddomain.md)

