---
title: Connect pilot pool to legacy Edge Servers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Connect pilot pool to legacy Edge Servers
ms:assetid: c3b67220-5705-47f6-852e-415204f3626c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721875(v=OCS.15)
ms:contentKeyID: 49733808
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Connect pilot pool to legacy Edge Servers

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

After deploying Lync Server 2013, you need to configure a federation route for your site. In order to use the federated route that is being used by Lync Server 2010, Lync Server 2013 must be configured to use this route.

To enable the Lync Server 2013 site to use the Director and Edge Server of the Lync Server 2010 deployment, use Topology Builder to associate the legacy Edge pool.

<div>

## To associate the legacy Edge pool by using Topology Builder

1.  Open **Topology Builder**.

2.  Select your site, which is directly below the **Lync Server** node.

3.  On the **Actions** menu, click **Edit Properties**.

4.  In the left pane, select **Federation route**.

5.  Under **Site federation route assignment**, select **Enable SIP federation**, and then select the Lync Server 2010 Director, or the Lync Server 2010 Edge Server if no Director is listed.
    
    ![Edit Properties, Federation route page](images/JJ721875.5f1d04c3-c724-426d-b27d-3fe89c6c5cfb(OCS.15).jpg "Edit Properties, Federation route page")  

6.  Click **OK** to close the **Edit Properties** page.

7.  In Topology Builder, under the Lync Server 2013 node, navigate to the **Standard Edition server** or **Enterprise Edition Front End pools**, right-click the pool, and then click **Edit Properties**.

8.  Under **Associations**, select the check box next to **Associate Edge pool (for media components)**.

9.  From the list, select the legacy Edge Server.
    
    ![Edit Properties dialog, selecting the legacy Edge](images/JJ721875.feae8156-540e-4804-bb0a-2b5736ec2900(OCS.15).jpg "Edit Properties dialog, selecting the legacy Edge")  

10. Click **OK** to close the **Edit Properties** page.

11. In **Topology Builder**, select the top-most node, **Lync Server**.

12. From the **Action** menu, click **Publish Topology**, and then click **Next**.

13. When the **Publishing wizard** completes, click **Finish**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

