---
title: "Get-CsTenantFederationConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e5f836d0-6066-4c23-9594-6e3f1cbd39ef
description: "Returns information about the federation configuration settings for your Microsoft Lync Online tenants. Federation configuration settings are used to determine which domains (if any) your users are allowed to communicate with."
---

# Get-CsTenantFederationConfiguration
[]
Returns information about the federation configuration settings for your Microsoft Lync Online tenants. Federation configuration settings are used to determine which domains (if any) your users are allowed to communicate with. 
  
The **Get-CsTenantFederationConfiguration** cmdlet can only be used with Lync Online.
  
```
Get-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-LocalStore] [-Verbose] Get-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-Filter <String>] [-LocalStore] [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Exercise 1 returns federation configuration information for the tenant with the tenant ID "bf19b7db-6960-41e5-a139-2aa373474354". Tenant IDs can be retrieved using a command similar to this:
  
Get-CsTenant | Select-Object TenantID
  
```
Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"
```

Note that the Tenant parameter is optional. You can also call Get-CsTenantFederationConfiguration by using this syntax:
  
```
Get-CsTenantFederationConfiguration
```

### Example 2

In Example 2, information is returned for all the domains found on the federation allowed list for the tenant bf19b7db-6960-41e5-a139-2aa373474354. (The allowed list represents all the domains that the tenant is allowed to federate with.) To do this, the command first calls the **Get-CsTenantFederationConfiguration** cmdlet to return federation information for the specified tenant. That information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty to "expand" the property AllowedList. Expanding a property simply means displaying all the information stored in that property onscreen, and in an easy-to-read format.
  
```
Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty AllowedList
```

### Example 3

The preceding command returns federation configuration for all the tenants currently in use in the organization. To carry out this task, the command first calls the **Get-CsTenant** cmdlet without any parameters; that returns a collection of all the available tenants. That collection is then piped to the **ForEach-Object** cmdlet. ForEach-Object takes each tenant in the collection and calls the **Get-CsTenantFederationConfiguration** cmdlet, using the property value TenantID (returned by the **Get-CsTenant** cmdlet) to represent the tenant ID.
  
```
Get-CsTenant | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId}
```

### Example 4

In Example 4, federation configuration information is only returned for tenants that do not allow federation with public users. To do this, the command first calls the **Get-CsTenant** cmdlet without any parameters in order to return a collection of all the tenants configured for use in the organization. That collection is piped to the **ForEach-Object** cmdlet, which takes each tenant in the collection and then uses the **Get-CsTenantFederationConfiguration** cmdlet to return federation configuration information. The entire set of federation configuration information is then piped to the **Where-Object** cmdlet, which picks out only those tenants where the AllowPublicUsers property is equal to (-eq) $False.
  
```
Get-CsTenant | Select-Object TenantId | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId} | Where-Object {$_.AllowPublicUsers -eq $False}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:
  
- Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.
    
- Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.
    
The **Get-CsTenantFederationConfiguration** cmdlet provides a way for administrators to return federation information for their Lync Online tenants. This cmdlet can also be used to review the allowed and blocked lists, lists which are used to specify domains that users can and cannot communicate with. However, administrators must use the **Get-CsTenantPublicProvider** cmdlet in order to see which public IM and presence providers users are allowed to communicate with.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection of tenant federation configuration settings. Because each tenant is limited to a single, global collection of federation configuration settings there is no need to use the Filter parameter. However, this is valid syntax for the **Get-CsTenantFederationConfiguration** cmdlet: <br/> Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Filter "g\*"  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the collection of tenant federation configuration settings to be returned. Because each tenant is limited to a single, global collection of federation settings there is no need include this parameter when calling the **Get-CsTenantFederationConfiguration** cmdlet. If you do choose to use the Identity parameter you must also include the Tenant parameter. For example: <br/> Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Identity "global"  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the tenant federation configuration data from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose federation settings are being returned. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Lync Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsTenantFederationConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsTenantFederationConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

