---
title: "Get-CsTopology"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ad52f545-b8dd-411e-8584-b6e29fe8ef18
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTopology
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about your Lync Server infrastructure, including internal domains, sites, clusters, computers, services, and back-end instances of SQL Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTopology [-AsXml <SwitchParameter>] [-LocalStore <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns complete details for your Lync Server topology. This is done by calling the **Get-CsTopology** cmdlet without any additional parameters. 
  
```
Get-CsTopology
```

### EXAMPLE 2

Example 2 returns information about the computers found in your Lync Server topology. To do this, the command first calls the **Get-CsTopology** cmdlet to return the complete Lync Server topology. This information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to extract and display detailed information for all the computers included in that topology. 
  
```
Get-CsTopology | Select-Object -ExpandProperty Machines
```

### EXAMPLE 3

The command shown in Example 3 returns information about your Lync Server topology and then saves that information to an XML file. To carry out this task, the command first calls the **Get-CsTopology** cmdlet, along with the AsXml parameter; that causes the data to be returned as formatted XML. That formatted data is then piped to the **Out-File** cmdlet, which saves the information to the file C:\Logs\Topology.xml. 
  
```
Get-CsTopology -AsXML | Out-File C:\Logs\Topology.xml
```

## Detailed Description
<a name="sectionSection1"> </a>

The **Get-CsTopology** cmdlet returns information about how Lync Server has been set up and configured. Called without any additional parameters, the cmdlet provides an overview of your Lync Server infrastructure; in that scenario, the cmdlet gives you an overall view of such things as your domains, your sites, and the computers running Lync Server services and server roles. Alternatively, you can pass the output of the **Get-CsTopology** cmdlet to the **Select-Object** cmdlet; this enables you to access detailed information about a portion of your topology. For example, the following command provides detailed information regarding the SQL Server instances used by Lync Server: 
  
Get-CsTopology | Select-Object -ExpandProperty SqlInstances
  
You can also use the AsXml parameter to return detailed information about your entire topology in XML format.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsTopology** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AsXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns topology information in XML format. By combining the **Get-CsTopology** cmdlet, the AsXml parameter, and the **Out-File** cmdlet, you can export your topology to an XML file.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the topology data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsTopology** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsTopology** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Enable-CsTopology](enable-cstopology.md)
  
[Publish-CsTopology](publish-cstopology.md)
  
[Test-CsTopology](test-cstopology.md)

