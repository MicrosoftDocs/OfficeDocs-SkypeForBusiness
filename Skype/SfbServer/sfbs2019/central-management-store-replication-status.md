---
title: "Central management store replication status in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 1/26/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f514f88d-986b-4e45-b79b-e04a7616c1fe
description: "When an administrator makes a change of some kind to Lync Server (for example, when an administrator creates a new voice policy or changes the Address Book Server configuration settings) that change is recorded in the Central Management store. In turn, the change must then be replicated to all the computers that are running Lync Server services or server roles."
---

# Central management store replication status in Lync Server 2013
[]
When an administrator makes a change of some kind to Lync Server (for example, when an administrator creates a new voice policy or changes the Address Book Server configuration settings) that change is recorded in the Central Management store. In turn, the change must then be replicated to all the computers that are running Lync Server services or server roles. 
  
To replicate data, the Master Replicator (running on the Central Management Server) creates a snapshot of the changed configuration data. A copy of this snapshot is then sent to each computer that is running Lync Server services or server roles. On those computers, a replication agent receives the snapshot and uploads the changed data. The agent then sends the Master Replicator a message reporting the latest replication status. 
  
The Get-CsManagementStoreReplicationStatus cmdlet enables you to verify the replication status for any (or all) of the Lync Server computers in your organization. 
  
Who can run this cmdlet? By default, members of the following groups are authorized to run the Get-CsManagementStoreReplicationStatus cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. 
  
To return a list of all RBAC roles this cmdlet was assigned to (including any custom RBAC roles that you have created yourself), run the following command from the Windows PowerShell prompt: 
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsManagementStoreReplicationStatus"}
```

## See also

#### 

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

