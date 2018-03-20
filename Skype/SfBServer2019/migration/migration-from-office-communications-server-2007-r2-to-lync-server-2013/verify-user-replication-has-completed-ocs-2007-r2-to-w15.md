---
title: "Verify user replication has completed [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 199dc9de-b555-468f-a42a-9e92ea6c9053
description: "When running the Move-CsLegacyUser cmdlet, you may experience a failure due to user information between Active Directory Domain Services (AD DS) and the Lync Server 2013 databases being out of sync because the initial replication is incomplete. The time it takes for the successful completion of the Lync Server 2013 User Replicator service's initial synchronization depends on the number of domain controllers that are hosted in the Active Directory forest that hosts the Lync Server 2013 pool. The Lync Server 2013 User Replicator service initial synchronization process occurs when the Lync Server 2013 Front End Server is started for the first time. After that, the synchronization is then based on the User Replicator interval. Complete the following steps to verify user replication has completed before running the Move-CsLegacyUser cmdlet."
---

# Verify user replication has completed [OCS 2007 R2 to W15]
[]
When running the **Move-CsLegacyUser** cmdlet, you may experience a failure due to user information between Active Directory Domain Services (AD DS) and the Lync Server 2013 databases being out of sync because the initial replication is incomplete. The time it takes for the successful completion of the Lync Server 2013 User Replicator service's initial synchronization depends on the number of domain controllers that are hosted in the Active Directory forest that hosts the Lync Server 2013 pool. The Lync Server 2013 User Replicator service initial synchronization process occurs when the Lync Server 2013 Front End Server is started for the first time. After that, the synchronization is then based on the User Replicator interval. Complete the following steps to verify user replication has completed before running the **Move-CsLegacyUser** cmdlet. 
  
## To verify that user replication has completed

1. From the Lync Server 2013 Front End server, click the **Start** menu, and then click **Run**. 
    
2. Enter **eventvwr.exe** and then click **OK**.
    
3. In Event Viewer, click **Applications and Services logs** to expand it, and then select Lync Server. 
    
4. In the **Actions** pane click **Filter Current Log**.
    
5. From the **Event sources** list, click **LS User Replicator**.
    
6. In **\<All Event IDs\>** enter **30024** and then click **OK**. 
    
7. In the filtered events list, on the **General** tab, look for an entry that states user replication has completed successfully. 
    

