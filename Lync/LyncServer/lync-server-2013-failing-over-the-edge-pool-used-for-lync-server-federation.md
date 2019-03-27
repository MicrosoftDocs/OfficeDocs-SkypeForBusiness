---
title: 'Lync Server 2013: Failing over the Edge pool used for Lync Server federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Failing over the Edge pool used for Lync Server federation
ms:assetid: 5c9da0f2-7429-40bb-bb3c-5cc4ecb5a13d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688071(v=OCS.15)
ms:contentKeyID: 49733665
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failing over the Edge pool used for Lync Server federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

If the Edge pool where you have Lync Server federation configured goes down, you must change federation to use a different Edge pool for federation to work.

<div>

## Failing Over the Edge Pool Used for Lync Server Federation

1.  On a Front End server, open Topology Builder. Expand **Edge pools**, then right click the Edge server or Edge server pool that is currently configured for Federation. Select **Edit properties**.

2.  In **Edit Properties** under **General**, clear **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

3.  Expand **Edge pools**, then right click the Edge server or Edge server pool that you now want to use for Federation. Select **Edit properties**.

4.  In **Edit Properties** under **General**, select **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

5.  Click **Action**, select **Topology**, select **Publish**. When prompted on **Publish the topology**, click **Next**. When the Publish is finished, click **Finish**.

6.  On the Edge server, open the Lync Server Deployment wizard. Click **Install or Update Lync Server System**, then click **Setup or Remove Lync Server Components**. Click **Run Again**.

7.  At Setup Lync Server components, click **Next**. The summary screen will show actions as they are executed. Once the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment.
    
    If the site containing the failed Edge pool contains Front End Servers that are still running, you must update the Web Conferencing Service and A/V Conferencing Service on these Front End pools to use an Edge pool in a remote site that is still running. For more information, see [Changing the Edge pool associated with a Front End pool in Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md).

</div>

<div>

## See Also


[Failing over the Edge pool used for XMPP federation in Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)  
[Failing back the Edge pool used for Lync Server federation or XMPP federation in Lync Server 2013](lync-server-2013-failing-back-the-edge-pool-used-for-lync-server-federation-or-xmpp-federation.md)  


[Edge Server disaster recovery in Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

