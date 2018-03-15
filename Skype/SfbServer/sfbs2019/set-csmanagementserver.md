---
title: "Set-CsManagementServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6607580d-f111-4dff-961a-71525bf2e482
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsManagementServer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies the replication port used by the Lync Server Central Management service. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsManagementServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplicationServicePort <UInt16>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 connects to the Central Management service with the Identity ManagementServer:atl-cs-001.litwareinc.com and sets the replication service port to port 5076.
  
```
Set-CsManagementServer -Identity "ManagementServer:atl-cs-001.litwareinc.com" -ReplicationServicePort 5076
```

## Detailed Description
<a name="sectionSection1"> </a>

The Central Management service is responsible for replicating data between the Central Management store and computers running Lync Server services or server roles. The Central Management service runs on a single Front End pool (or a single Standard Edition server) and facilitates replication throughout the Lync Server infrastructure. 
  
The **Set-CsManagementServer** cmdlet enables you to specify the port that the Central Management service uses for replication. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsManagementServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsManagementServer"} 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the Central Management service. For example: -Identity "ManagementServer:atl-cs-001.litwareinc.com".  <br/> Note that you can leave off the prefix "ManagementServer:" when specifying a Central Management Server. For example: -Identity "atl-cs-001.litwareinc.com".  <br/> |
| _ReplicationServicePort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for the replication port used by the Central Management service.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsManagementServer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsManagementServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayManagementServer object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsService](get-csservice.md)
  
[Move-CsManagementServer](move-csmanagementserver.md)

