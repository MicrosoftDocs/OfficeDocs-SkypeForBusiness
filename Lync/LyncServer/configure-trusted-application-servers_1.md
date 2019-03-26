---
title: Configure trusted application servers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure trusted application servers
ms:assetid: 47a9e72e-566c-4c23-bec2-760a3098a974
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204865(v=OCS.15)
ms:contentKeyID: 48184056
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

_**Topic Last Modified:** 2012-10-04_

In a mixed environment, if you create a new trusted application server after merging the legacy Office Communications Server topology with Lync Server 2013, and you define a new trusted application server using Topology Builder, you must set the next hop pool to be a Lync Server 2013 pool. In a merged environment, both the legacy Office Communications Server pool and the Lync Server 2013 pool appear in the drop down list. Selecting the legacy pool is *not* supported.

<div>

## To select Lync Server 2013 as next hop when creating a Trusted application server

1.  Open an existing topology in Topology Builder.

2.  In the left pane, right click **Trusted application servers** and click **New Trusted Application Pool**.

3.  Enter the **Pool FQDN** of the trusted application pool and select whether it will be a single-server or multiple-server deployment.

4.  Click **Next**.

5.  On the **Select the next hop** page, from the list, select the Lync Server 2013 Front End pool.
    
    ![Define New Trusted Application Pool dialog](images/JJ204865.ecfe2bb8-758b-4b36-8146-573005c4ab09(OCS.15).jpg "Define New Trusted Application Pool dialog")  

6.  Click **Finish**.

7.  Select the top node **Lync Server** and from the **Actions** pane, select **Publish**.

8.  Verify the **Trusted Application Pool** was created successfully and is associated with the correct Front End pool.

</div>

</div>

<span> </span>

</div>

</div>

</div>

