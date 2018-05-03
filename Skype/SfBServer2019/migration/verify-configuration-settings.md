---
title: "Verify configuration settings"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 51c2d1d9-63f7-43ab-88ca-b8913da7cede
description: "You can validate the replication of configuration information to the Edge server by running the Lync Server 2013 Get-CsManagementStoreReplicationStatus cmdlet on the internal computer on which the Central Management store is located, or on any domain joined computer on which Lync Server 2013 Core Components (OcsCore.msi) is installed."
---

# Verify configuration settings
[]
You can validate the replication of configuration information to the Edge server by running the Lync Server 2013 **Get-CsManagementStoreReplicationStatus** cmdlet on the internal computer on which the Central Management store is located, or on any domain joined computer on which Lync Server 2013 Core Components (OcsCore.msi) is installed. 
  
Initial results may indicate the status as "False" instead of "True" for replication. If so, run the **Invoke-CsManagementStoreReplication** cmdlet and allow time for the replication to complete before running the **Get-CsManagementStoreReplicationStatus** again. 
  

