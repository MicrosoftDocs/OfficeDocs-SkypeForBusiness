---
title: "Get-CsSite"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0e5fd5b8-17aa-433d-9915-3b88281fa2c2
description: "Returns information about the sites created as part of your Skype for Business Server 2015 infrastructure. Sites represent a collection of Skype for Business Server 2015 pools and are typically designed around geographic regions. Skype for Business Server 2015 includes two types of sites: data center sites and remote sites (branch sites). This cmdlet was introduced in Lync Server 2010."
---

# Get-CsSite
[]
Returns information about the sites created as part of your Skype for Business Server 2015 infrastructure. Sites represent a collection of Skype for Business Server 2015 pools and are typically designed around geographic regions. Skype for Business Server 2015 includes two types of sites: data center sites and remote sites (branch sites). This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 retrieves information for all your Skype for Business Server 2015 sites.
  
```
Get-CsSite
```

### EXAMPLE 2

In Example 2, information is returned for a single site: the site with the Identity Redmond.
  
```
Get-CsSite -Identity "Redmond"
```

### EXAMPLE 3

The command shown in Example 3 returns information for your central site. To carry out this task, the command first calls the **Get-CsSite** cmdlet in order to return a collection of all the sites configured for use in your organization. This collection is then piped to the **Where-Object** cmdlet, which picks out the one site where the SiteType property is equal to "CentralSite".
  
```
Get-CsSite | Where-Object {$_.SiteType -eq "CentralSite"}
```

### EXAMPLE 4

Example 4 displays the list of pools found in the Redmond site. To do this, the command first retrieves complete information for the Redmond site, and then pipes that data to the **Select-Object** cmdlet. In turn, the **Select-Object** cmdlet uses the ExpandProperty parameter to "expand" the value of the Pools property. Expanding a property value means that all the values stored in that property will be displayed on the screen in an easy-to-read format.
  
```
Get-CsSite -Identity "Redmond" | Select-Object -ExpandProperty Pools
```

## Detailed Description

Lync Server 2010 introduced a new concept to the topology: sites. Sites (which should not be confused with Active Directory sites or Exchange sites) are a collection of Skype for Business Server 2015 pools and servers that are typically organized according to geography and network bandwidth. For example, if all your computers in Redmond are located on the same local area network with high-speed, low-latency connections, you might designate a Redmond site that encompasses those computers. If your computers in Dublin are located on their own local area network, and share high-speed, low-latency connections, then you might create a separate Dublin site as well. Sites play a key role in Skype for Business Server 2015 management: most policies and settings can be configured at the site scope, making it easy to do such things as apply one set of dial plans to users in Redmond and a completely different set of dial plans to users in Dublin.
  
The **Get-CsSite** cmdlet enables you to return information about all the sites in your organization, including information about the pools that make up each of those sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of the site (or sites) to be returned. For example, this syntax returns all the pools that have an Identity that include the string value "Dublin":  <br/>  `-Filter "*Dublin*"` <br/> Note that you cannot use both Filter and Identity in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Name of the site to be returned. Note that you should specify just the site name; for example:  <br/>  `-Identity "Redmond"` <br/> Do not use the format "site:Redmond" when specifying the Identity.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsSite** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsSite** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite object.
  
## See also

#### 

[Set-CsSite](set-cssite.md)

