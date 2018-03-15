---
title: "Set-CsAllowedDomain"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d5b25b66-2b11-40ef-9ea4-efcae0b610e6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsAllowedDomain
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies property values for a domain (or domains) included on the list of domains approved for federation. After a domain has been approved for federation (by being added to the allowed list), your users can exchange instant messages and presence information with people who have accounts in the federated domain. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsAllowedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 modifies the Comment property for the allowed domain with the Identity "fabrikam.com". This is done by including the Comment parameter and the appropriate parameter value: "Contact: Ken Myer (kenmyer@fabrikam.com)".
  
```
Set-CsAllowedDomain -Identity fabrikam.com -Comment "Contact: Ken Myer (kenmyer@fabrikam.com)"
```

### EXAMPLE 2

Example 2 modifies the Comment and MarkForMonitoring properties for all of the allowed domains that have the string value "fabrikam" somewhere in their Identity. To carry out this task, the command first calls the **Get-CsAllowedDomain** cmdlet and the Filter parameter. The filter value "*fabrikam*" instructs the **Get-CsAllowedDomain** cmdlet to return any domain where the Identity includes the string value "fabrikam". (For example, this command returns domains such as fabrikam.com, us.fabrikam.net, and fabrikam-users.org). The filtered collection is then piped to the **Set-CsAllowedDomain** cmdlet, which modifies for Comment property and sets the MarkForMonitoring property to True ($True) for each item in the collection. 
  
```
Get-CsAllowedDomain -Filter *fabrikam* | Set-CsAllowedDomain -Comment "Contact: Ken Myer (kenmyer@fabrikam.com)" -MarkForMonitoring $True
```

### EXAMPLE 3

The command shown in Example 3 modifies all of the domains on the allowed list that are not currently monitored by Monitoring Server. (That is, all of the domains where the MarkForMonitoring property is set to False.) To do this, the **Get-CsAllowedDomain** cmdlet is called without any additional parameters in order to retrieve a collection of all the domains on the allowed list. That collection is piped to the **Where-Object** cmdlet, which selects only those domains where MarkForMonitoring is equal to False. The filtered collection is then piped to the **Set-CsAllowedDomain** cmdlet, which sets the MarkForMonitoring property for each domain in the collection to True. 
  
```
Get-CsAllowedDomain | Where-Object {$_.MarkForMonitoring -eq $False} | Set-CsAllowedDomain -MarkForMonitoring $True
```

### EXAMPLE 4

Example 4 adds a generic comment ("Need contact information.") to each domain on the allowed list where the Comment property currently has no value. To carry out this task, the command first calls the **Get-CsAllowedDomain** cmdlet to retrieve a collection of all the domains on the allowed list. This collection is then piped to the **Where-Object** cmdlet, which picks out those domains where the Comment property is equal to a null value. That filtered collection is then piped to the **Set-CsAllowedDomain** cmdlet, which modifies the Comment property for each item in the collection. 
  
```
Get-CsAllowedDomain | Where-Object {$_.Comment -eq $Null} | Set-CsAllowedDomain -Comment "Need contact information."
```

## Detailed Description
<a name="sectionSection1"> </a>

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another by using SIP applications such as Lync. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
Setting up direct federation with another organization involves several tasks. To begin with, you must enable your servers running the Lync Server Access Edge service to allow federation. In addition, the other organization must enable federation with you; federation cannot be established unless both parties agree to the relationship.
  
To set up a federated relationship you might also need to manage two federation-related lists: the allowed list and the blocked list. The allowed list represents the organizations you have chosen to federate with. If a domain appears on the allowed list then (depending on your configuration settings) your users will be able to exchange instant messages and presence information with users who have accounts in that federated domain. Conversely, the blocked list represents domains that users are expressly forbidden from federating with; for example, messages sent from a blocked domain will automatically be rejected by Lync Server.
  
The **Set-CsAllowedDomain** cmdlet provides a way for you to modify property values for any domain on the list of allowed domains. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsAllowedDomain** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsAllowedDomain"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Comment_ <br/> |Optional  <br/> |System.String  <br/> |Optional string value that provides additional information about the domain being modified. For example, you might add a Comment that provides contact information for the federated domain.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the allowed domain for which the property values are being modified. For example:  <br/> -Identity fabrikam.com  <br/> |
| _Instance_ <br/> |Optional  <br/> |Blocked Domain object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MarkForMonitoring_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the federation connection between your domain and the remote domain will be monitored by Monitoring Server. By default, MarkForMonitoring is set to False, meaning that the connection will not be monitored.  <br/> This property will be ignored if you have not deployed Monitoring Server.  <br/> |
| _ProxyFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (for example, proxy-server.fabrikam.com) of the SIP proxy server deployed in the domain being added to the allowed list. This property is optional: if it is not specified then DNS SRV discovery procedures will be used to determine the location of the SIP proxy server.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain object. The **Set-CsAllowedDomain** cmdlet accepts pipelined instances of the allowed domain object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsAllowedDomain** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAllowedDomain](get-csalloweddomain.md)
  
[New-CsAllowedDomain](new-csalloweddomain.md)
  
[Remove-CsAllowedDomain](remove-csalloweddomain.md)
  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

