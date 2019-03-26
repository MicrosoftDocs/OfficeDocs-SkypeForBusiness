---
title: 'Lync Server 2013: Add branch sites to your topology'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Add branch sites to your topology
ms:assetid: b9c35fb0-0081-4aeb-8f95-ac2fcc6c3335
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412905(v=OCS.15)
ms:contentKeyID: 48185216
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add branch sites to your topology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Branch sites represent physical branch offices that are connected to your main offices over a WAN link. To add a branch site to your Lync topology, perform this procedure at the central site.

<div>

## To add branch sites to your topology

1.  Click **Start**, click **All Programs**, click **Microsoft Lync Server**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the central site, right-click **Branch Sites**, and then click **New Branch Site**.

3.  In the **Define New Branch Site** dialog box, click **Name**, and then type the name of the branch site.

4.  (Optional) Click **Description**, and then type a meaningful description for the branch site.

5.  Click **Next**.

6.  (Optional) In the next **Define New Branch Site** dialog box, do any of the following:
    
      - Click **City**, and then type the name of the city in which the branch site is located.
    
      - Click **State/Region**, and then type the name of the state or region in which the branch site is located.
    
      - Click **Country Code**, and then type the two-digit calling code for the country/region in which the branch site is located.

7.  Click **Next**, and then do one of the following:
    
      - If you are using a Survivable Branch Appliance or Server at this site, be sure that the **Open the New Survivable Wizard when this wizard closes** check box is selected, click **Finish**, and then follow the directions in the wizard that opens. For information about wizard items, see [Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).
    
      - If you are not using a Survivable Branch Appliance or Server at this site, clear the **Open the New Survivable Wizard when this wizard closes** check box, and then click **Finish**.

8.  Repeat the previous steps for each branch site that you want to add to the topology.

**Next step:**

For Survivable Branch Appliances or Servers: [Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

For non-resilient PSTN connectivity: [Define a PSTN gateway for a branch site in Lync Server 2013](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md), [Configure a trunk with media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md), or [Configure a trunk without media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

