---
title: 'Add Lync Server 2013 Survivable Branch Appliance branch site to your topology'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Add Lync Server 2013 Survivable Branch Appliance branch site to your topology
ms:assetid: d3142a37-4606-456d-8ea9-6cc0e51e55f3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721896(v=OCS.15)
ms:contentKeyID: 49733830
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add Lync Server 2013 Survivable Branch Appliance branch site to your topology

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-07_

Microsoft Lync Server 2013 Survivable Branch Appliances (SBA) cannot be associated to a Microsoft Lync Server 2010 Front End pool as a backup Registrar. The SBA must be associated with a Microsoft Lync Server 2013 Front End pool. These steps assume a Microsoft Lync Server 2013 SBA. Perform this procedure at the central site.

<div>

## To add branch sites with Microsoft Lync Server 2013 SBA to your topology

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the central site, expand **Branch Sites**, and then click **New Branch Site**.

3.  In the **Define New Branch Site** dialog box, click **Name**, and then type a name for the new branch site.

4.  (Optional) Click **Description**, and then type a meaningful description for the branch site.

5.  Click **Next**.

6.  (Optional) In the next **Define New Branch Site** dialog box, do any of the following:
    
      - Click **City**, and then type the name of the city in which the branch site is located.
    
      - Click **State/Region**, and then type the name of the state or region in which the branch site is located.
    
      - Click **Country Code**, and then type the two-digit calling code for the country/region in which the branch site is located.

7.  Click **Next**, and then do one of the following:
    
      - If you are using a Survivable Branch Appliance or Survivable Branch Server at this site, be sure that the **Open the New Survivable Wizard when this wizard closes** check box is selected.
    
      - If you are not using a Survivable Branch Appliance or Survivable Branch Server at this site, clear the **Open the New Survivable Wizard when this wizard closes** check box.
    
      - Click **Finish**, and then follow the directions in the wizard that opens. For information about wizard items, see [Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).

8.  Repeat the previous steps for each branch site that you want to add to the topology.

</div>

<div>

## See Also


[Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)  
[Define a PSTN gateway for a branch site in Lync Server 2013](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md)  
[Configure a trunk with media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configure a trunk without media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

