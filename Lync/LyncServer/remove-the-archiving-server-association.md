---
title: Remove the Archiving server association
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove the Archiving server association
ms:assetid: dabac157-71ee-4afe-b0b6-4a083d165ffb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721903(v=OCS.15)
ms:contentKeyID: 49733837
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove the Archiving server association

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

To remove an Archiving Server, you need to change or clear the dependency on the associated Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server. You edit the properties of the Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server to remove the dependency. After you clear the dependency and you delete the server in Topology Builder, you are notified that the associated database store object in Topology Builder will also be deleted.

<div>

## To remove the Archiving Server association

1.  Open the Lync Server 2013 Front End Server, open Topology Builder.

2.  Navigate to the Lync Server 2010 node.

3.  In Topology Builder, expand **Enterprise Edition Front End pools**, **Standard Edition Front End Servers**, or **Branch sites**, based on where the Archiving Server is defined.

4.  If you have Survivable Branch Server associated, expand **Branch sites**, expand the branch site name, and then expand **Survivable Branch Appliances**.
    
    <div>
    

    > [!NOTE]  
    > <STRONG>Survivable Branch Appliances</STRONG> in the user interface applies to both Survivable Branch Server and Survivable Branch Appliance.

    
    </div>

5.  Right-click the pool, server, or device that is associated with the Archiving Server, and then click **Edit Properties**.

6.  In **Edit Properties**, under **General**, under **Associations**, clear the **Associate Archiving Server** check box, and then click **OK**.

7.  Repeat the previous step for any other pool, server or device associated with the Archiving Server that you want to remove.

8.  Right-click the Archiving Server, and then click **Delete**.

9.  On **Delete Dependent Stores**, click **OK**.

10. Publish the topology, check replication status, and then run the Lync Server Deployment Wizard as needed.

</div>

</div>

<span> </span>

</div>

</div>

</div>

