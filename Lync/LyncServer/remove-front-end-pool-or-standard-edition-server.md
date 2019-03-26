---
title: Remove Front End pool or Standard Edition server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove Front End pool or Standard Edition server
ms:assetid: 83c39a36-49a1-4ac6-9cc5-b0e441b1fdec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688115(v=OCS.15)
ms:contentKeyID: 49733713
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove Front End pool or Standard Edition server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

This topic guides you through the process of removing a Front End pool or a Standard Edition Front End Server. When you remove a Front End pool, you remove each Front End Server that belongs to the pool as a part of the pool removal process. When you remove a Standard Edition Front End Server, you must remove the SQL Store definition from Topology Builder.

<div>

## To remove a Front End Server pool

1.  Open Topology Builder.

2.  Navigate to the Lync Server 2010 node.

3.  Expand **Enterprise Edition Front End pools**, expand the Front End pool, right-click the Front End pool that you want to remove, and then click **Delete**.

4.  Publish the topology, check replication status, and then run the Lync Server Deployment Wizard as needed.

</div>

<div>

## To remove a Standard Edition Front End server

1.  Open Topology Builder.

2.  Navigate to the Lync Server 2010 node.

3.  Expand **Standard Edition Front End servers**, right-click the Front End Server that you want to remove, and then click **Delete**.

4.  Expand **SQL stores**, right-click the SQL Server database that is associated with the Standard Edition Front End Server, and then click **Delete**.
    
    <div>
    

    > [!IMPORTANT]  
    > You must remove the definition of the collocated SQL Server databases from the Standard Edition Front End Server.

    
    </div>

5.  Publish the topology, check replication status, and then run the Lync Server Deployment Wizard as needed.

</div>

</div>

<span> </span>

</div>

</div>

</div>

