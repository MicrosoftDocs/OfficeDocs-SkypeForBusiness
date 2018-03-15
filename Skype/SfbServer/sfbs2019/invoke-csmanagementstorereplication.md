---
title: "Invoke-CsManagementStoreReplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fa3dece3-afd8-4669-94f9-fc3b70201e81
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Invoke-CsManagementStoreReplication
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Forces Lync Server replication services to send complete configuration data to the specified computers. This is done by deleting the replication status of the computers from the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Invoke-CsManagementStoreReplication [-ReplicaFqdn <String>] [-Force <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **Invoke-CsManagementStoreReplication** cmdlet is called without any parameters. This forces replication to take place on all Lync Server computers. 
  
```
Invoke-CsManagementStoreReplication
```

### EXAMPLE 2

In Example 2, the ReplicaFqdn parameter is used when calling the **Invoke-CsManagementStoreReplication** cmdlet. That causes replication to take place only on the computer atl-cs-001.litwareinc.com. 
  
```
Invoke-CsManagementStoreReplication -ReplicaFqdn atl-cs-001.litwareinc.com
```

## Detailed Description
<a name="sectionSection1"> </a>

When an administrator makes a change to Lync Server (for example, when an administrator creates a new voice policy or changes the Address Book server configuration settings) that change is recorded in the Central Management store. In turn, the change must then be replicated to all the computers running Lync Server services or server roles.
  
In order to replicate data, the Master Replicator (running on the Central Management Server) creates a snapshot of the modified configuration data; a copy of this snapshot is then sent to each computer running Lync Server services or server roles. On those computers, a replication agent receives the snapshot and uploads the modified data; the agent then sends the Master Replicator a message reporting the latest replication status.
  
Replication typically requires no human intervention; in fact, it's usually best to let the Master Replicator handle the replication process. However, there might be occasions when you need to forcibly initiate replication on a computer (or a group of computers) without waiting for the standard replication cycle to run its course. Should such an occasion arise, you can forcibly replicate information to a computer by using the **Invoke-CsManagementStoreReplication** cmdlet. 
  
Typically, replication works on an incremental basis: when data is replicated, only the changes are replicated, not the complete set of configuration data. However, when you call the **Invoke-CsManagementStoreReplication** cmdlet, you force a complete replication of all the data rather than the more typical replication of changes only. Note that replication will not necessarily take place immediately when you call the **Invoke-CsManagementStoreReplication** cmdlet. Instead, there could be a two to three minute delay as changes are processed by the Master Replicator. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Invoke-CsManagementStoreReplication** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Invoke-CsManagementStoreReplication"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _ReplicaFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the computer where replication should be initiated. For example: -ReplicaFqdn "atl-cs-001.litwareinc.com".  <br/> If this parameter is not included, then replication will be initiated on all your Lync Server computers.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Invoke-CsManagementStoreReplication** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Invoke-CsManagementStoreReplication** cmdlet does not return any objects. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

