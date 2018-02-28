---
title: "Set-CsTenantFederationConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 5/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e13c2f55-7a68-4174-a0da-5eec8c65f64c
description: "Manages federation configuration settings for your Microsoft Lync Online tenants. These settings are used to determine which domains (if any) your users are allowed to communicate with."
---

# Set-CsTenantFederationConfiguration
[]
Manages federation configuration settings for your Microsoft Lync Online tenants. These settings are used to determine which domains (if any) your users are allowed to communicate with.
  
The **Set-CsTenantFederationConfiguration** cmdlet can only be used with Skype for Business Online.
  
```
Set-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Force] [-Verbose] [-WhatIf] [-Confirm]Set-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Instance <PSObject>] [-Force] [-Verbose] [-WhatIf] [-Confirm]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 disables communication with public providers for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowPublicUsers $False
```

Note that the Tenant parameter is optional. If you leave off that parameter Windows PowerShell will automatically insert the correct Tenant ID based on your connection information.
  
### Example 2

Example 2 shows how you can disable public provider communication for all the tenants in your organization. To do this, the command first calls the **Get-CsTenant** cmdlet to return a collection of all the available tenants. That collection is then piped to the **Select-Object** cmdlet, which picks out only the TenantId property for each item in the collection. That collection of tenant IDs is then piped to the **ForEach-Object** cmdlet. The F **orEach-Object** cmdlet then takes each tenant ID and runs the **Set-CsTenantFederationConfiguration** cmdlet against that ID, setting the AllowPublicUsers property for each tenant to False ($False).
  
```
Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantId -AllowPublicUsers $False}
```

### Example 3

In Example 3, the domain fabrikam.com is assigned as the only domain on the blocked domains list for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". To do this, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a new domain object for fabrikam.com. This domain object is stored in a variable named $x.
  
The second command in the example then uses the **Set-CsTenantFederationConfiguration** cmdlet to update the blocked domains list. Using the Replace method ensures that the existing blocked domains list will be replaced by the new list: a list that contains only the domain fabrikam.com.
  
```
$x = New-CsEdgeDomainPattern "fabrikam.com"
Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Replace=$x}
```

### Example 4

The commands shown in Example 4 remove fabrikam.com from the list of domains blocked by the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". To do this, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a domain object for fabrikam.com. The resulting domain object is then stored in a variable named $x.
  
The second command in the example then uses the **Set-CsTenantFederationConfiguration** cmdlet and the Remove method to remove fabrikam.com from the blocked domains list for the specified tenant.
  
```
$x = New-CsEdgeDomainPattern "fabrikam.com"
Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Remove=$x}
```

### Example 5

The commands shown in Example 5 add the domain fabrikam.com to the list of domains blocked by the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". To add a new blocked domain, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a domain object for fabrikam.com. This object is stored in a variable named $x.
  
After the domain object has been created, the second command then uses the **Set-CsTenantFederationConfiguration** cmdlet and the Add method to add fabrikam.com to any domains already on the blocked domains list.
  
```
$x = New-CsEdgeDomainPattern "fabrikam.com"
Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Add=$x}
```

### Example 6

Example 6 shows how you can remove all the domains assigned to the blocked domains list for a given tenant. To do this, simply include the BlockedDomains parameter, and set the parameter value to null ($Null). When this command completes, the blocked domain list will be cleared for the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $Null
```

## Detailed Description
<a name="DetailedDescription"> </a>

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:
  
> Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.
    
> Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.
    
Administrators can use the **Set-CsTenantFederationConfiguration** cmdlet to enable and disable federation with other domains and federation with public providers. In addition, this cmdlet can be used to expressly indicate the domains that users can communicate with and/or the domains that users are not allowed to communicate with. However, administrators must use the **Set-CsTenantPublicProvider** cmdlet in order to indicate the public IM and presence providers that users can and cannot communicate with.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowedDomains_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.IAllowedDomainsChoice  <br/> |Domain objects (created by using the **New-CsEdgeAllowList** cmdlet or the **New-CsEdgeAllowAllKnownDomains** cmdlet) that represent the domains that users are allowed to communicate with. If the **New-CsEdgeAllowAllKnownDomains** cmdlet is used then users can communicate with any domain that does not appear on the blocked domains list. If the **New-CsEdgeAllowList** cmdlet is used then users can only communicate with domains that have been added to the allowed domains list. <br/> Note that string values cannot be passed directly to the AllowedDomains parameter. Instead, you must create an object reference using the **New-CsEdgeAllowList** cmdlet or the **New-CsEdgeAllowAllKnownDomains** cmdlet and then use the object reference variable as the parameter value. <br/> |
| _AllowFederatedUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be potentially allowed to communicate with users from other domains. If this property is set to False then users cannot communicate with users from other domains regardless of the values assigned to the AllowedDomains and BlockedDomains properties.  <br/> |
| _AllowPublicUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be potentially allowed to communicate with users who have accounts on public IM and presence providers such as Windows Live, Yahoo, and AOL. The collection of public providers that users can actually communicate with is managed by using the Set-CsTenantPublicProvider cmdlet.  <br/> |
| _BlockedDomains_ <br/> |Optional  <br/> |System.Boolean  <br/> |If the AllowedDomains property has been set to AllowAllKnownDomains, then users will be allowed to communicate with users from any domain except domains that appear in the blocked domains list. If the AllowedDomains property has not been set to AllowAllKnownDomains, then the blocked list is ignored, and users can only communicate with domains that have been expressly added to the allowed domains list.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the collection of tenant federation configuration settings to be modified. Because each tenant is limited to a single, global collection of federation settings there is no need include this parameter when calling the **Set-CsTenantFederationConfiguration** cmdlet. If you do choose to use the Identity parameter you must also include the Tenant parameter. For example: <br/> Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Identity "global"  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _SharedSipAddressSpace_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, indicates that the users homed on Lync Online use the same SIP domain as users homed on the on-premises version of Lync Server. The default value is False, meaning that the two sets of users gave have different SIP domains.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose federation settings are being modified. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Lync Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsTenantFederationConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsTenantFederationConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

