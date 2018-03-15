---
title: "Get-CsManagementStoreReplicationStatus"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea7162d6-d1e5-4301-b162-38da4e422293
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsManagementStoreReplicationStatus
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the Lync Server replication process; this includes information on whether replication is currently up to date for your Lync Server computers. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsManagementStoreReplicationStatus [-ReplicaFqdn <String>] [-CentralManagementStoreStatus <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **Get-CsManagementStoreReplicationStatus** cmdlet is called without any parameters; that returns the replication status (up to date or not up to date) for all Lync Server computers. 
  
```
Get-CsManagementStoreReplicationStatus
```

### EXAMPLE 2

Example 2 returns a collection of all the computers where replication is not up to date. This is done by first using the **Get-CsManagementStoreReplicationStatus** cmdlet to retrieve a collection containing the replication status for all the servers. This collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to computers where the UpToDate property is equal to False. 
  
```
Get-CsManagementStoreReplicationStatus | Where-Object {$_.UpToDate -eq $False}
```

### EXAMPLE 3

In Example 3, returned data is limited to a single computer: atl-cs-001.litwareinc.com/
  
```
Get-CsManagementStoreReplicationStatus -ReplicaFqdn atl-cs-001.litwareinc.com
```

### EXAMPLE 4

Example 4 returns information about the computers that were last replicated prior to 8:00 P.M. on August 11, 2010. To do this, the **Get-CsManagementStoreReplicationStatus** cmdlet is first called to return replication information for all your Lync Server computers. This information is then piped to the **Where-Object** cmdlet, which selects only those computers where the LastUpdateCreation property is less than 8:00 P.M. on August 11, 2010 (8/11/2010 8:00 P.M.). To return information about computers that were last replicated after 8:00 P.M. on August 11, 2010, use the -gt (greater than) operator: 
  
Where-Object {$_.LastUpdateCreation -gt "8/11/2010 8:00 PM"}
  
The dates specified in this example use the U.S. English format for date-time values. Dates should be specified using a format compatible with your Regional and Language Options.
  
```
Get-CsManagementStoreReplicationStatus | Where-Object {$_.LastUpdateCreation -lt "8/11/2010 8:00 PM"}
```

### EXAMPLE 5

The command shown in Example 5 uses the CentralManagementStoreStatus parameter to return detailed information about the current status of the Central Management store. This includes the fully qualified domains names of the Active Master and the File Transfer Agent services, as well as the date and time of the last heartbeat detected for each of those services. 
  
```
Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus
```

## Detailed Description
<a name="sectionSection1"> </a>

When an administrator makes a change of some kind to Lync Server (for example, when an administrator creates a new voice policy or changes the Address Book Server configuration settings) that change is recorded in the Central Management store. In turn, the change must then be replicated to all the computers running Lync Server services or server roles. 
  
In order to replicate data, the Master Replicator (running on the Central Management Server) creates a snapshot of the modified configuration data; a copy of this snapshot is then sent to each computer running Lync Server services or server roles. On those computers, a replication agent receives the snapshot and uploads the modified data; the agent then sends the Master Replicator a message reporting the latest replication status.
  
The **Get-CsManagementStoreReplicationStatus** cmdlet enables you to verify the replication status for any (or all) of the Lync Server computers in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsManagementStoreReplicationStatus** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsManagementStoreReplicationStatus"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CentralManagementStoreStatus_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns additional information about the current status of the Central Management store, including a list of active replicas and deleted replicas, as well as the location of the Active Master and the File Transfer Agent services.  <br/> |
| _ReplicaFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the computer for which the replication status is to be checked. For example: -ReplicaFqdn "atl-cs-001.litwareinc.com".  <br/> If this parameter is not included, then replication status information for all your Lync Server computers will be returned.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsManagementStoreReplicationStatus** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

By default, the **Get-CsManagementStoreReplicationStatus** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.ReplicaState object. If the CentralManagementStoreStatus parameter is used, then the cmdlet returns instances of the Microsoft.Rtc.Management.Xds.CentralManagementStoreStatusResult object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)

