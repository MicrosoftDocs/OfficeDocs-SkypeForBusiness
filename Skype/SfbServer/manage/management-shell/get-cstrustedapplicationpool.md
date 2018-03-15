---
title: "Get-CsTrustedApplicationPool"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f8dc4ad7-fc32-482b-a1cb-5ba106df3344
description: "Retrieves settings for one or more pools that contain the computers that host trusted applications. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsTrustedApplicationPool
 
Retrieves settings for one or more pools that contain the computers that host trusted applications. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTrustedApplicationPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 retrieves all pools within the Skype for Business Server 2015 deployment that have been defined as trusted application pools.
  
```
Get-CsTrustedApplicationPool
```

### EXAMPLE 2

In this example, we've used the Identity parameter to ensure we retrieve only one trusted application pool, in this case the pool with the FQDN TrustPool.litwareinc.com.
  
```
Get-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com
```

### EXAMPLE 3

This example retrieves all trusted application pools that contain the site TrustPool in the pool FQDN. The Filter parameter is used with a value of \*:TrustPool.\*. This filter string will search the Identity values of all trusted application pools for those that contain the string ":TrustPool.". For example, this command will retrieve the pool with the Identity value TrustedApplicationPool:TrustPool.litwareinc.com.
  
```
Get-CsTrustedApplicationPool -Filter *:TrustPool.*
```

### EXAMPLE 4

The Filter parameter searches only on Identity, which in the case of trusted application pools is the service ID in the format TrustedApplicationPool:<FQDN>. This example searches for pools based on service ID in the format <site>-ExternalServer-<id>; for example, Redmond1-ExternalServer-1. This allows us to find trusted pools homed on a specific site. The example begins by calling the **Get-CsTrustedApplicationPool** cmdlet with no parameters, which retrieves a collection of all trusted application pools. This collection is then piped to the **Where-Object** cmdlet, which narrows down the collection to only those pools where the service ID ($_.ServiceId) matches the wildcard string (-like) Redmond1*. The result will be a collection of all trusted application pools with FQDNs beginning with the string Redmond1, such as Redmond1-ExternalServer-1, Redmond1-ExternalServer-2, and Redmond1-ExternalServer-3.
  
```
Get-CsTrustedApplicationPool | Where-Object {$_.ServiceId -like "Redmond1*"}
```

## Detailed Description

It is recommended that computers that are running trusted applications within a Skype for Business Server 2015 deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. This cmdlet retrieves one or more pools that have been defined as trusted application pools.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string containing one or more wildcard characters that is used to search for a pool with an Identity that matches the wildcard string. For example, specifying the string \*Redmond\* would retrieve all trusted application pools with identities containing the string Redmond, such as TrustedApplicationPool:Redmond.litwareinc.com.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The fully qualified domain name (FQDN) or service ID of the pool for which you want to retrieve settings.  <br/> |
| _PoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |The FQDN of the pool you want to retrieve. This behaves the same as the Identity parameter, except that Identity also accepts a service ID.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Retrieves one or more objects of type Microsoft.Rtc.Management.Xds.DisplayExternalServer.
  
## See also

#### 

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)
  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)
  
[Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)

