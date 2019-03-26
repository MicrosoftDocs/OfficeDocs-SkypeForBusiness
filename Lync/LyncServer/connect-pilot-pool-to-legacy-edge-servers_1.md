---
title: Connect pilot pool to legacy Edge Servers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Connect pilot pool to legacy Edge Servers
ms:assetid: 9ed13c41-f3ab-4e1d-beb6-a00152c541e2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205136(v=OCS.15)
ms:contentKeyID: 48185003
ms.date: 07/23/2014
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

_**Topic Last Modified:** 2012-10-02_

After deploying Lync Server 2013, a federation route for this site is not configured. In order to use the federated route that is being used by Office Communications Server 2007 R2, Lync Server 2013 must be configured to use this route.

To enable the Lync Server 2013 site to use the Director and Edge Server of the BackCompatSite, use Topology Builder to associate the legacy Edge pool.

<div>

## To associate the legacy Edge pool by using Topology Builder

1.  Open the pilot pool topology in Topology Builder.

2.  Select your Lync Server 2013 site.

3.  On the **Action** menu, click **Edit Properties**.

4.  Under **Site federation route assignment**, select **Enable SIP federation**, and then select the Office Communications Server 2007 R2 Director, or the Office Communications Server 2007 R2 Edge Server if no Director is listed.
    
    ![Edit Properties dialog, Federation route page](images/JJ205136.bc13014b-3578-4d9e-9ff7-bdd09130b676(OCS.15).jpg "Edit Properties dialog, Federation route page")  

5.  Click **OK** to close the **Edit Properties** page.

6.  In Topology Builder, under the Lync Server 2013 node, navigate to the **Standard Edition server** or **Enterprise Edition Front End pools**, right-click the pool, and then click **Edit Properties**.

7.  Under **Associations**, select the check box next to **Associate Edge pool (for media components)**.

8.  From the list, select the Edge Server interface for the BackCompatSite.
    
    ![Edit Properties dialog, General page](images/JJ205136.75045212-03ca-4b82-8337-5dacb487094f(OCS.15).jpg "Edit Properties dialog, General page")  

9.  Click **OK** to close the **Edit Properties** page.

10. In **Topology Builder**, select the top-most node, **Lync Server**.

11. From the **Action** menu, click **Publish Topology**, and then click **Next**.

12. When the **Publishing wizard** completes, click **Finish**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

