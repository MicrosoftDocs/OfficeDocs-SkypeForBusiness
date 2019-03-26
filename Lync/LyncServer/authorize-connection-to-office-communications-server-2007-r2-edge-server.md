---
title: Authorize connection to Office Communications Server 2007 R2 Edge Server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Authorize connection to Office Communications Server 2007 R2 Edge Server
ms:assetid: 14f6798a-28d6-4b3d-8734-942192e1bbf5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204702(v=OCS.15)
ms:contentKeyID: 48183493
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Authorize connection to Office Communications Server 2007 R2 Edge Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

For each Lync Server 2013 Front End Server or Standard Edition server in your pilot pool, you must update the list of internal servers that are authorized to connect to the Office Communications Server 2007 R2 Edge Server. Without these updates, external audio/visual (A/V) conferencing for users joining by using the legacy Edge Server will not work.

<div>

## To Authorize Connection to Office Communications Server 2007 R2 Edge Server

1.  From the Office Communications Server 2007 R2 Edge Server, from the **Administrative Tools** group, open the **Computer Management** snap-in.

2.  In the console tree, expand **Services and Applications**.

3.  Right-click **Office Communications Server 2007 R2**, and then click **Properties**.

4.  Click the **Internal** tab.

5.  Under **Add Server**, click **Add**.

6.  In the **Add Office Communications Server** dialog box, enter the appropriate information:
    
      - Specify the fully qualified domain name (FQDN) of each Lync Server 2013 Front End Server or Standard Edition server, and Lync Server 2013 pool.
    
      - Specify the FQDN of the Lync Server 2013 Director if you configured a static route on the pool that specifies the next hop computer by its FQDN.

7.  After you have added an entry for each Lync Server 2013, Front End Server, Standard Edition server, pool, and Director, click **Apply** and then click **OK** to close the Properties page.

</div>

</div>

<span> </span>

</div>

</div>

</div>

