---
title: "Verify connectivity between internal servers and Edge Servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 219f706e-2b8a-46c5-b394-c384240eef50
description: "In Lync Server 2013, a separate validation wizard was available to help validate connectivity between Edge Servers and internal servers. In Lync Server 2013 validation of connectivity is done automatically when you install your Edge Servers."
---

# Verify connectivity between internal servers and Edge Servers in Lync Server 2013
[]
In Lync Server 2013, a separate validation wizard was available to help validate connectivity between Edge Servers and internal servers. In Lync Server 2013 validation of connectivity is done automatically when you install your Edge Servers. 
  
You can validate the replication of configuration information to the edge by running the Windows PowerShell **Get-CsManagementStoreReplicationStatus** cmdlet on the internal computer on which the Central Management store is located (or any domain joined computer on which Lync Server 2013 Core Components (OcsCore.msi) is installed. Initial results may indicate the status as "False" instead of "True" for replication. If so, run the **Invoke-CsManagementStoreReplication** cmdlet and allow time for the replication to complete before running the **Get-CsManagementStoreReplicationStatus** again. 
  
You can verify external user connectivity separately, including using the Office Communications Server Remote Connectivity Analyzer to verify remote user connectivity. For details, see [Verify connectivity for external users in Lync Server 2013](verify-connectivity-for-external-users.md).
  

