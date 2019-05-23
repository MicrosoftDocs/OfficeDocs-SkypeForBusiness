---
title: "Verify configuration settings"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can validate the replication of configuration information to the Edge server by running the Skype for Business Server 2019 Get-CsManagementStoreReplicationStatus cmdlet on the internal computer on which the Central Management store is located, or on any domain joined computer on which Skype for Business Server 2019 Core Components (OcsCore.msi) is installed."
---

# Verify configuration settings

You can validate the replication of configuration information to the Edge server by running the Skype for Business Server 2019 **Get-CsManagementStoreReplicationStatus** cmdlet on the internal computer on which the Central Management store is located, or on any domain-joined computer on which Skype for Business Server 2019 Core Components (OcsCore.msi) is installed. 
  
Initial results may indicate the status as "False" instead of "True" for replication. If so, run the **Invoke-CsManagementStoreReplication** cmdlet and allow time for the replication to complete before running the **Get-CsManagementStoreReplicationStatus** again. 
  

