---
title: "Get-CsTenant"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b642117-5ca7-4a5b-bca7-16b0ae694ae2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTenant
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about the Skype for Business Online tenants that have been configured for use in your organization. Tenants represent groups of online users. In many cases, you might need only a single tenant. However, if different groups of users have different management needs, Skype for Business Online provides support for a single organization having multiple tenants.
  
Get-CsTenant can only be used with Skype for Business Online.
  
```
Get-CsTenant [[-Identity] <OUIdParameter>] [-Filter <String>] [-ResultSize <Unlimited`1>] [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the tenants configured for use in the organization.
  
```
Get-CsTenant
```

### Example 2

In Example 2, information is returned for a single tenant: the tenant with the Identity "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
Get-CsTenant -Identity "bf19b7db-6960-41e5-a139-2aa373474354"
```

### Example 3

The preceding command shows an alternate way to return information for a single tenant; in this example, that's done by including the Filter parameter and the filter value {DisplayName -eq "Fabrikam"}. That syntax returns information only for the tenant that has the display name Fabrikam.
  
```
Get-CsTenant -Filter {DisplayName -eq "Fabrikam"}
```

### Example 4

The command shown in Example 4 returns information for all the tenants that have a ServiceInstance equal to "LitwareincCommunicationsOnline/San Antonio". To do this, the command includes the Filter parameter and the filter value {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}. That filter value limits returned data to tenants that have a ServiceInstance property equal to (-eq) "LitwareincCommunicationsOnline/San Antonio".
  
```
Get-CsTenant -Filter {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}
```

### Example 5

Example 5 returns information for all tenants that have a country or region display name equal to Australia. This is done by using the Filter parameter and the parameter value {CountryOrRegionDisplayName -eq "Australia"}.
  
```
Get-CsTenant -Filter {CountryOrRegionDisplayName -eq "Australia"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Online, tenants represents groups of users who have accounts homed on the service. Many organizations will require only a single tenant in which to house all their user accounts. However, Skype for Business Online management is often performed on a tenant-by-tenant basis; that means that all the users in the same tenant will have the same voice policy, the same federation configuration settings, and so on. If you need to manage some users in one way and other users in another way, you might consider using multiple tenants, each with its own collection of policies and settings.
  
Regardless of the number of tenants you have, you can return information about these tenants by using the **Get-CsTenant** cmdlet. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to return data by using Active Directory attributes and without having to specify the full Active Directory distinguished name. For example, to retrieve a tenant by using the tenant display name, use syntax similar to this:  <br/> Get-CsTenant -Filter {DisplayName -eq "FabrikamTenant"}  <br/> To return all tenants that use a Fabrikam domain use this syntax:  <br/> Get-CsTenant -Filter {Domains -like "\*fabrikam\*"}  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax is used by the Where-Object cmdlet.  <br/> You cannot use both the Identity parameter and the Filter parameter in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Active Directory distinguished name of the tenant. For example:  <br/> -Identity "OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=litwareinc,dc=com"  <br/> If you do not include either the Identity or the Filter parameter then the **Get-CsTenant** cmdlet will return information about all your tenants.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1  <br/> |Enables you to limit the number of records returned by the cmdlet. For example, to return seven tenants (regardless of the number of tenants that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which 7 users will be returned.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the tenants to 7 but you have only three contacts in your forest, the command will return those three tenants and then complete without error.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Get-CsTenant** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.TenantObject object as well as string values representing the Identity of a Skype for Business Online tenant (for example "OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=vdomain,dc=com"). 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsTenant** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.TenantObject object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOnlineUser](get-csonlineuser.md)

