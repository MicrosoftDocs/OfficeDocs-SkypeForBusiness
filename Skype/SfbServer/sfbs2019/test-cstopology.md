---
title: "Test-CsTopology"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06ffa245-f1c7-46b7-9be6-5b291deda5c1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsTopology
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies service activation and group permissions for your installation of Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsTopology [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-Service <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 validates the entire Lync Server topology.
  
```
Test-CsTopology
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Report parameter is included to specify the location (C:\Logs\Topology.xml) where the output file should be written.
  
```
Test-CsTopology -Report "C:\Logs\Topology.xml"
```

### EXAMPLE 3

In Example 3, the **Test-CsTopology** cmdlet is used to validate a single service: Registrar:atl-cs-001.litwareinc.com. 
  
```
Test-CsTopology -Service "Registrar:atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

The **Test-CsTopology** cmdlet provides a way for you to verify that Lync Server is functioning correctly at a global level. By default, the cmdlet checks your entire Lync Server infrastructure, verifying that the required services are running and that the appropriate permissions have been set for these services and for the universal security groups created when you install Lync Server. 
  
In addition to verifying the validity of Lync Server as a whole, the **Test-CsTopology** cmdlet also lets you check the validity of a specific service. For example, this command checks the state of the A/V Conferencing Server on the pool atl-cs-001.litwareinc.com: 
  
Test-CsTopology -Service "ConferencingServer:atl-cs-001.litwareinc.com".
  
Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsTopology"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Test-CsTopology** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\Topology.html"  <br/> |
| _Service_ <br/> |Optional  <br/> |System.String  <br/> |When present, the **Test-CsTopology** cmdlet limits its validation checks to the specified service. (Note that you can only specify one service at a time when using the Service parameter.) Services should be specified using the appropriate service ID; for example, this syntax refers to the Registrar service on the atl-cs-001.litwareinc.com pool: -Service "Registrar:atl-cs-001.litwareinc.com".  <br/> If this parameter is not included then the entire topology will be validated.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Test-CsTopology** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsTopology** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Enable-CsTopology](enable-cstopology.md)
  
[Get-CsTopology](get-cstopology.md)
  
[Publish-CsTopology](publish-cstopology.md)

