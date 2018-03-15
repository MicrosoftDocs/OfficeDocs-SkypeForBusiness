---
title: "Get-CsSite"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0e5fd5b8-17aa-433d-9915-3b88281fa2c2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsSite
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the sites created as part of your Lync Server infrastructure. Sites represent a collection of Lync Server pools and are typically designed around geographic regions. Lync Server includes two types of sites: data center sites and remote sites (branch sites). This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 retrieves information for all your Lync Server sites.
  
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
<a name="sectionSection1"> </a>

Lync Server 2010 introduced a new concept to the Lync Server topology: sites. Sites (which should not be confused with Active Directory sites or Microsoft Exchange Server sites) are a collection of Lync Server pools and servers that are typically organized according to geography and network bandwidth. For example, if all your computers in Redmond are located on the same local area network with high-speed, low-latency connections, you might designate a Redmond site that encompasses those computers. If your computers in Dublin are located on their own local area network, and share high-speed, low-latency connections, then you might create a separate Dublin site as well. Sites play a key role in Lync Server management: most policies and settings can be configured at the site scope, making it easy to do such things as apply one set of dial plans to users in Redmond and a completely different set of dial plans to users in Dublin.
  
The **Get-CsSite** cmdlet enables you to return information about all the sites in your organization, including information about the pools that make up each of those sites. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsSite** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsSite"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of the site (or sites) to be returned. For example, this syntax returns all the pools that have an Identity that include the string value "Dublin": -Filter "\*Dublin\*".  <br/> Note that you cannot use both Filter and Identity in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Name of the site to be returned. Note that you should specify just the site name; for example: -Identity "Redmond". Do not use the format "site:Redmond" when specifying the Identity.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsSite** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsSite** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsSite](set-cssite.md)

