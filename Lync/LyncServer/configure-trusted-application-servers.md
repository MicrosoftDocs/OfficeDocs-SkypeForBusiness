---
title: Configure trusted application servers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure trusted application servers
ms:assetid: 20c3815f-3048-4940-8c0f-cdfcd0801d5d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204735(v=OCS.15)
ms:contentKeyID: 48183592
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure trusted application servers

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-11_

In a mixed environment, if you create a new trusted application server, you must set the next hop pool to be a Lync Server 2013 pool. In a mixed environment, both the legacy Lync Server 2010 pool and the Lync Server 2013 pool appear in the drop down list. Selecting the legacy pool is not supported.

**Select Lync Server 2013 as next hop when creating a Trusted application server**

1.  Open Topology Builder.

2.  In the left pane, right click **Trusted application servers** and click **New Trusted Application Pool**.

3.  Enter the **Pool FQDN** of the trusted application pool and select whether it will be a single-server or multiple-server.

4.  Click **Next**.

5.  On the **Select the next hop** page, from the list, select the Lync Server 2013 Front End pool.

6.  Click **Finish**.

7.  Select the top node **Lync Server** and from the **Action** menu, select **Publish**.
    
    Verify the **Trusted Application Pool** has been created successfully and is associated with the correct Front End pool.

</div>

<span> </span>

</div>

</div>

</div>

