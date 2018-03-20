---
title: "New-CsEdgeAllowList"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 21a6d546-9e03-485c-b7ec-9deb778f2b01
description: "Enables administrators to specify the domains that their users will be allowed to communicate with. The New-CsEdgeAllowList cmdlet, which can be used only with Microsoft Lync Online, must be used in conjunction with the New-CsEdgeDomainPattern cmdlet and the Set-CsTenantFederationConfiguration cmdlet."
---

# New-CsEdgeAllowList
 
Enables administrators to specify the domains that their users will be allowed to communicate with. The **New-CsEdgeAllowList** cmdlet, which can be used only with Microsoft Lync Online, must be used in conjunction with the **New-CsEdgeDomainPattern** cmdlet and the **Set-CsTenantFederationConfiguration** cmdlet.
  
```
New-CsEdgeAllowList [-AllowedDomain <PSListModifier>] [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 assign the domain fabrikam.com to the allowed domains list for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". To do this, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a domain object for fabrikam.com; this object is stored in a variable named $x. After the domain object has been created, the **New-CsEdgeAllowList** cmdlet is used to create a new allowed list containing only the domain fabrikam.com.
  
With the allowed domain list created, the final command in the example can then use the **Set-CsTenantFederationConfiguration** cmdlet to configure fabrikam.com as the only domain on the allowed domain list for the specified tenant.
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
$newAllowList = New-CsEdgeAllowList -AllowedDomain $x
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList
```

Note that the Tenant parameter is only required in a hybrid deployment. If you are only connected to Lync Online then Tenant parameter can be omitted.
  
### Example 2

Example 2 shows how you can add multiple domains to an allowed domains list. This is done by calling the **New-CsEdgeDomainPattern** cmdlet multiple times (one for each domain to be added to the list), and storing the resulting domain objects in separate variables. Each of those variables can then be added to the allow list created by the **New-CsEdgeAllowList** cmdlet simply by using the AllowedDomain parameter and separating the variables name by using commas:
  
$newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y
  
```
$x = New-CsEdgeDomainPattern -Domain "contoso.com"
$y = New-CsEdgeDomainPattern -Domain "fabrikam.com"
$newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList
```

### Example 3

In Example 3, all domains are removed from the allowed domains list. To do this, the first command in the example uses the **New-CsEdgeAllowList** cmdlet to create a blank list of allowed domains; this is accomplished by setting the AllowedDomain property to a null value ($Null). The resulting object reference ($newAllowList) is then used in conjunction with the **Set-CsTenantFederationConfiguration** cmdlet to remove all the domains from the allowed domain list for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
$newAllowList = New-CsEdgeAllowList -AllowedDomain $Null
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList
```

## Detailed Description
<a name="DetailedDescription"> </a>

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:
  
- Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with..
    
- Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo
    
Federation is managed, in part, by using allowed domain and blocked domain lists. The allowed domain list specifies the domains that users are allowed to communicate with; the blocked domain list specifies the domains that users are not allowed to communicate with. By default, users can communicate with any domain that does not appear on the blocked list. However, administrators can modify this default setting and limit communication to domains that are on the allowed domains list.
  
Lync Online does not allow you to directly modify the allowed list or the blocked list; for example, you cannot use a command similar to this one, which passes a string value representing a domain name to the allowed domains list:
  
```
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"
```

Instead, you must use either the **New-CsEdgeAllowAllKnownDomains** cmdlet or the **New-CsEdgeAllowList** cmdlet to create a domain object and then pass that domain object to the **Set-CsTenantFederationConfiguration** cmdlet. The **New-CsEdgeAllowAllKnownDomains** cmdlet is used if you want to allow users to communicate with all domains except for those expressly specified on the blocked domains list. The **New-CsEdgeAllowList** cmdlet is used if you want to limit user communication to a specified collection of domains. In that case, users will only be allowed to communicate with domains that appear on the allowed domains list.
  
To add a single domain (fabrikam.com) to the allowed domain list, you need to use a set of command similar to these:
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
$newAllowList = New-CsEdgeAllowList -AllowedDomain $x
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList
```

When this command finishes executing, users will only be allowed to communicate with users from fabrikam.com domain.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowedDomain_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Object reference to the new domain (or set of domains) to be added to the allowed domain list. Domain object references must be created by using the **New-CsEdgeDomainPattern** cmdlet. Multiple domain objects can be added by separating the object references using commas. For example: <br/> -AllowedDomain $x,$y  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsEdgeAllowList** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsEdgeAllowList** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowList object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)
  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)
  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

