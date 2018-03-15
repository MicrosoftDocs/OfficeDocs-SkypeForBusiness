---
title: "Get-CsPool"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e0911c68-9a0a-461a-88d6-c610c6cd996c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPool
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the pools used in your deployment of Lync Server. Pools are a collection of computers in a site that all run the same set of Lync Server services. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns all the pools found in your deployment of Lync Server.
  
```
Get-CsPool
```

### EXAMPLE 2

Example 2 displays detailed information about the computers found in each of your pools. This is done by calling the **Get-CsPool** cmdlet, and then piping the returned data to the **Select-Object** cmdlet. The ExpandProperty parameter is then used to "expand" the value of the Computers property. The Computers property is an array of objects representing each computer in the pool. When you expand the Computers property you get back detailed information about each of these computers. 
  
```
Get-CsPool | Select-Object -ExpandProperty Computers
```

### EXAMPLE 3

In Example 3, the Identity parameter is used to restrict the returned data to the pool that has the Identity atl-cs-001.litwareinc.com.
  
```
Get-CsPool -Identity atl-cs-001.litwareinc.com
```

### EXAMPLE 4

Example 4 returns all the pools found in the Redmond site. To do this, the command uses the Site parameter; the parameter value "Redmond" limits the returned data to pools where the Site property is equal to Redmond.
  
```
Get-CsPool -Site "Redmond"
```

### EXAMPLE 5

The command shown in Example 5 returns a collection of all the pools that do not have any Lync Server services installed. To carry out this task, the command first calls the **Get-CsPool** cmdlet without any parameters; that returns a collection of all the pools currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out all the pools where the Services.Count property is equal to 0. If the Count equals 0, that means that there are no Lync Server services configured for that pool. 
  
```
Get-CsPool | Where-Object {$_.Services.Count -eq 0}
```

## Detailed Description
<a name="sectionSection1"> </a>

In Lync Server, a pool is one or more computers in the same site that run the same set of services. For example, if you have one server running the Mediation Server service in the Redmond site, then you would have a Mediation Server pool consisting of that one computer. If you have two computers running Mediation Server in the Redmond site, then you would have a Mediation Server pool consisting of two computers. The number of pools used in your organization depends on the number of servers you have and the different services run by those servers.
  
The **Get-CsPool** cmdlet enables you to retrieve information about each pool in use in your organization, including information about the services running on each of those pools. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPool** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPool"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of the pool (or pools) to be returned. For example, this syntax returns all the pools that have an Identity that ends with the string value ".fabrikam.com": -Filter "\*.fabrikam.com".  <br/> Note that you cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the pool to be returned. For example: -Identity atl-cs-001.litwareinc.com.  <br/> If this parameter is not present, then all the pools in your organization will be returned.  <br/> |
| _Site_ <br/> |Optional  <br/> |System.String  <br/> |Returns all the pools found on the specified site. The site in question should be referenced using the site's DisplayName (for example, Redmond) rather than the site Identity (for example, site:Redmond). For example: -Site "Redmond". You can retrieve the display names for your sites by running this command:  <br/> Get-CsSite | Select-Object Identity, DisplayName  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsPool** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsPool** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Cluster object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsSite](get-cssite.md)
  
[Get-CsTopology](get-cstopology.md)

