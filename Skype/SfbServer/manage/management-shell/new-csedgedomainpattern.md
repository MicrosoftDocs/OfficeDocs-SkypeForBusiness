---
title: "New-CsEdgeDomainPattern"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 653bc148-c22b-4ad4-afdd-17aaeaa299d2
description: "Used to specify a domain that will be added or removed from the set of domains enabled for federation or the set of domains disabled for federation. You must use the New-CsEdgeDomainPattern cmdlet when modifying the allowed or blocked domain lists. String values (such asfabrikam.com) cannot be directly passed to the cmdlets used to manage either of these lists."
---

# New-CsEdgeDomainPattern
[]
Used to specify a domain that will be added or removed from the set of domains enabled for federation or the set of domains disabled for federation. You must use the **New-CsEdgeDomainPattern** cmdlet when modifying the allowed or blocked domain lists. String values (such as "fabrikam.com") cannot be directly passed to the cmdlets used to manage either of these lists.
  
The **New-CsEdgeDomainPattern** cmdlet can only be used with Lync Online.
  
```
New-CsEdgeDomainPattern -Domain <String> [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 demonstrates how you can assign a single domain to the blocked domains list for a specified tenant. To do this, the first command in the example creates a domain object for the domain fabrikam.com; this is done by calling the **New-CsEdgeDomainPattern** cmdlet and by saving the resulting domain object in a variable named $x. The second command then uses the **Set-CsTenantFederationConfiguration** cmdlet and the BlockedDomains parameter to configure fabrikam.com as the only domain blocked by the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x
```

## Detailed Description
<a name="DetailedDescription"> </a>

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:
  
- Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.
    
- Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.
    
Federation is managed, in part, by using allowed domain and blocked domain lists. The allowed domain list specifies the domains that users are allowed to communicate with; the blocked domain list specifies the domains that users are not allowed to communicate with. By default, users can communicate with any domain that does not appear on the blocked list. However, administrators can modify this default setting and limit communication to domains that are on the allowed domains list.
  
Lync Online does not allow you to directly modify the allowed list or the blocked list; for example, you cannot use a command similar to this one, which passes a string value representing a domain name to the blocked domains list:
  
```
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains "fabrikam.com"
```

Instead, you must create a domain object by using the **New-CsEdgeDomainPattern** cmdlet, store that domain object in a variable (in this example, $x), then pass the variable name to the blocked domains list:
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the domain to be added to the allow list. For example:  <br/> -Domain "fabrikam.com"  <br/> Note that you cannot use wildcards when specifying a domain name.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsEdgeDomainPattern** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsEdgeDomainPattern** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DomainPattern object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)
  
[New-CsEdgeAllowList](new-csedgeallowlist.md)
  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

