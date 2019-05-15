---
title: Connect a Survivable Branch Appliance
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Connect a Survivable Branch Appliance
ms:assetid: fe3167e2-d1b1-4cd4-bf30-262e0e7d14e8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721948(v=OCS.15)
ms:contentKeyID: 49733886
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Connect a Survivable Branch Appliance

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Every Survivable Branch Appliance (SBA) is associated with a Front End pool which serves as a backup registrar for the SBA. When the Front End pool is migrated to Lync Server 2013, the SBA must be disassociated from the Lync Server 2010 Front End pool while the pool is upgraded, Once the pool has been migrated to Lync Server 2013, the SBA can be re-associated with the upgraded Front End pool. This involves deleting the SBA from the legacy Lync Server 2010 topology in Topology Builder and then adding the SBA to the Lync Server 2013 topology. Users homed on the legacy Lync Server 2010 SBA must first be moved to another Front End pool before removing the SBA from the topology. Once the SBA is added to the Lync Server 2013 topology, those users can then be moved back to the SBA. These steps are summarized below:

1.  Move branch users homed on the legacy SBA Lync Server 2010 to another Front End pool.

2.  Remove SBA from the legacy Lync Server 2010 topology to disconnect the existing Front End pool as a backup registrar.

3.  Add SBA to the Lync Server 2013 topology and configure this new Front End pool as the backup registrar.

4.  Move the branch users to the new Lync Server 2013 SBA.

**Add Lync Server 2010 SBA Branch Site to Your Topology**

1.  Open **Topology Builder**.

2.  In the left pane right-click **Branch sites**, and then click **New Branch Site**.

3.  In the **Define New Branch Site** dialog box, click **Name**, and then type the name of the branch site.

4.  (Optional) Click **Description**, and then type a meaningful description for the branch site.

5.  Click **Next**.

6.  (Optional) In the next **Define New Branch Site** dialog box, do any of the following:
    
    1.  Click **City**, and then type the name of the city in which the branch site is located.
    
    2.  Click **State/Region**, and then type the name of the state or region in which the branch site is located.
    
    3.  Click **Country Code**, and then type the two-digit calling code for the country/region in which the branch site is located.

7.  Click **Next**, and then do one of the following:
    
    1.  If you are using a Lync 2010 Survivable Branch Appliance or Server at this site, be sure to uncheck the **Open the New Survivable Wizard when this wizard closes** option. Click **Finish**.

8.  To associate the legacy Lync Server 2010 SBA to the Lync Server 2013 Front End pool:
    
    1.  Expand the branch site that has been created.
    
    2.  Right click on **Lync Server 2010** and then click **New**.
    
    3.  Click **Survivable Branch Appliance…**

9.  Follow the directions in the wizard that opens. For information about wizard items, see [Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).
    
    <div>
    

    > [!NOTE]  
    > A Lync Server 2010 Survivable Branch Appliance can only be associated with a Lync Server 2010 Monitoring Store.

    
    </div>

10. If you are not using a Survivable Branch Appliance or Server at this site, clear the **Open the New Survivable Wizard when this wizard closes** check box, and then click **Finish**.

11. Repeat the previous steps for each branch site you want to add to the topology.

</div>

<span> </span>

</div>

</div>

</div>

