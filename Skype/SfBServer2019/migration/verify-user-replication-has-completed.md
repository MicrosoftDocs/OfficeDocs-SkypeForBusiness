---
title: "Verify user replication has completed"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "When running the Move-CsUser cmdlet, you may experience a failure because user information between Active Directory Domain Services (AD DS) and the Skype for Business Server 2019 databases are out of sync because the initial replication is incomplete. The time it takes for the successful completion of the Skype for Business Server 2019 User Replicator service's initial synchronization depends on the number of domain controllers that are hosted in the Active Directory forest that hosts the Skype for Business Server 2019 pool. The Skype for Business Server 2019 User Replicator service initial synchronization process occurs when the Skype for Business Server 2019 Front End Server is started for the first time. After that, the synchronization is then based on the User Replicator interval. Complete the following steps to verify user replication has completed before running the Move-CsUser cmdlet."
---

# Verify user replication has completed

When running the **Move-CsUser** cmdlet, you may experience a failure if user information between Active Directory Domain Services (AD DS) and the Skype for Business Server 2019 databases are out of sync because the initial replication is incomplete. The time it takes for the successful completion of the Skype for Business Server 2019 User Replicator service's initial synchronization depends on the number of domain controllers that are hosted in the Active Directory forest that hosts the Skype for Business Server 2019 pool. The Skype for Business Server 2019 User Replicator service initial synchronization process occurs when the Skype for Business Server 2019 Front End Server is started for the first time. After that, the synchronization is based on the User Replicator interval. Complete the following steps to verify that user replication has completed before running the **Move-CsUser** cmdlet. 
  
### To verify that user replication has completed

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
2. Click the **Start** menu, and then click **Run**. 
    
3. Enter **eventvwr.exe**, and then click **OK**.
    
4. In Event Viewer, click **Applications and Services logs** to expand it, and then select Skype for Business Server. 
    
5. In the **Actions** pane, click **Filter Current Log**.
    
6. From the **Event sources** list, click **LS User Replicator**.
    
7. In **\<All Event IDs\>**, enter **30024**, and then click **OK**. 
    
8. In the filtered events list, on the **General** tab, look for an entry that states that user replication has completed successfully. 
    

