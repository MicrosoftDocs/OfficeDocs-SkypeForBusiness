---
title: "New-CsEdgeAllowAllKnownDomains"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f9416909-c328-41b3-9215-7ebd091b0ca0
description: "Enables Microsoft Lync Online federation with all domains except for those domains included on the blocked domains list."
---

# New-CsEdgeAllowAllKnownDomains
[]
Enables Microsoft Lync Online federation with all domains except for those domains included on the blocked domains list. 
  
This cmdlet can only be used with Lync Online.
  
```
New-CsEdgeAllowAllKnownDomains [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

The two commands shown in Example 1 configure the federation settings for the tenant with the Identity "bf19b7db-6960-41e5-a139-2aa373474354" to allow all known domains. To do this, the first command in the example uses the **New-CsEdgeAllowAllKnownDomains** cmdlet to create an instance of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains object; this instance is stored in a variable named $x. In the second command, the **Set-CsTenantFederationConfiguration** cmdlet is called along with the AllowedDomains parameter; using $x as the parameter value configures the federation settings to allow all known domains.
  
```
$x = New-CsEdgeAllowAllKnownDomains
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x
```

### Example 2

Example 2 demonstrates how you can configure all your tenants to allow communications with all the domains not explicitly shown on the blocked domains list. To do this, the first command in the example uses the **New-CsEdgeAllowAllKnownDomains** cmdlet to create an instance of the AllowAllKnownDomains object, an object stored in a variable named $x.
  
The second command in the example then uses the **Get-CsTenant** cmdlet to return a collection of all the available tenants. This collection is then piped to the **ForEach-Object** cmdlet. The **ForEach-Object** cmdlet, in turn, runs the **Set-CsTenantFederationConfiguration** cmdlet against each tenant in the collection, configuring the AllowedDomains property to allow all known domains.
  
```
$x = New-CsEdgeAllowAllKnownDomains
Get-CsTenant | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantID -AllowedDomains $x}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:
  
- Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.
    
- Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.
    
Federation is managed, in part, by using allowed domain and blocked domain lists. The allowed domain list specifies the domains that users are allowed to communicate with; the blocked domain list specifies the domains that users are not allowed to communicate with. By default, users can communicate with any domain that does not appear on the blocked list. However, administrators can modify this default setting and limit communication to domains that are on the allowed domains list.
  
Lync Online does not allow you to directly modify the allowed list or the blocked list; for example, you cannot use a command similar to this one, which passes a string value representing a domain name to the allowed domains list:
  
```
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"
```

Instead, you must use either the **New-CsEdgeAllowAllKnownDomains** cmdlet or the **New-CsEdgeAllowList** cmdlet to create a domain object and then pass that domain object to the **Set-CsTenantFederationConfiguration** cmdlet. The **New-CsEdgeAllowAllKnownDomains** cmdlet is used if you want to allow users to communicate with all domains except for those expressly specified on the blocked domains list. The N **ew-CsEdgeAllowList** cmdlet is used if you want to limit user communication to a specified collection of domains. In that case, users will only be allowed to communicate with domains that appear on the allowed domains list.
  
To configure federation with all known domains, use a set of commands similar to this:
  
```
$x = New-CsEdgeAllowAllKnownDomains
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|This cmdlet provides only common Windows PowerShell parameters.  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsEdgeAllowAllKnownDomains** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsEdgeAllowAllKnownDomains** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsEdgeAllowList](new-csedgeallowlist.md)
  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)
  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

