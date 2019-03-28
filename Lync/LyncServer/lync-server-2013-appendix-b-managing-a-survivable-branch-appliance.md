---
title: 'Lync Server 2013: Appendix B: Managing a Survivable Branch Appliance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: 'Appendix B: Managing a Survivable Branch Appliance'
ms:assetid: 2ec9d505-6d39-491c-9524-8cf36866b855
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425797(v=OCS.15)
ms:contentKeyID: 48183773
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Appendix B: Managing a Survivable Branch Appliance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

This topic describes the procedures for managing a Survivable Branch Appliance. Specifically, how to replace and rename a Survivable Branch Appliance, and how to change the Lync Server 2013 Front End pool that the Survivable Branch Appliance is associated with.

<div>

## To Replace a Survivable Branch Appliance

1.  Stop all Lync Server 2013 services on the Survivable Branch Appliance. (See the Survivable Branch Appliance vendor documentation.)

2.  (Recommended) Remove the Survivable Branch Appliance from the domain.

3.  Delete the Survivable Branch Appliance computer object in Active Directory Domain Services, by following these steps:
    
      - Log on to a member server as a member of the Enterprise Admins group.
    
      - Click **Start**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.
    
      - Right-click the Survivable Branch Appliance object, and click **Delete**.

4.  Add the Survivable Branch Appliance computer object again. (See [Add a Survivable Branch Appliance to Active Directory in Lync Server 2013](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md).)

5.  Wait for Active Directory replication to take place.

6.  Open the Lync Server Management Shell, and type **Enable-CSTopology**.

7.  Connect the new Survivable Branch Appliance to the network, and follow the steps in [Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) and [Deploy a Survivable Branch Appliance or Server with Lync Server 2013 - branch site task](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md).

</div>

<div>

## To Rename a Survivable Branch Appliance

1.  Move users to the central site. For details, see [Move users to another pool in Lync Server 2013](lync-server-2013-move-users-to-another-pool.md).

2.  Stop all Lync Server 2013 services on the Survivable Branch Appliance. (See the Survivable Branch Appliance vendor documentation.)

3.  Remove the Survivable Branch Appliance from the topology, by following these steps:
    
      - Click **Start**, click **All Programs**, click **Microsoft Lync Server**, and then click **Lync Server Topology Builder**.
    
      - In the console tree, expand **Branch Sites**, click the Survivable Branch Appliance, and then click **Delete** on the Action pane.

4.  Remove the Survivable Branch Appliance from the domain.

5.  Delete the Survivable Branch Appliance computer object in Active Directory, by following these steps:
    
      - Log on to a domain controller as a member of the Enterprise Admins group.
    
      - Click **Start**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.
    
      - Right-click the Survivable Branch Appliance object, and click **Delete**.

6.  Restore the Survivable Branch Appliance to factory defaults. (See the Survivable Branch Appliance vendor documentation.)

7.  Follow the steps in [Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) and [Deploy a Survivable Branch Appliance or Server with Lync Server 2013 - branch site task](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md).

8.  Move users to the renamed Survivable Branch Appliance. For details, see [Move users to another pool in Lync Server 2013](lync-server-2013-move-users-to-another-pool.md).

</div>

<div>

## To Change the Lync Server Front End Pool that the Survivable Branch Appliance Is Associated With

1.  Move users from the Survivable Branch Appliance to the Lync Server Front End pool at the central site. For details, see [Move users to another pool in Lync Server 2013](lync-server-2013-move-users-to-another-pool.md).

2.  Stop all Lync Server services on the Survivable Branch Appliance. (See the Survivable Branch Appliance vendor documentation).

3.  Update the Lync Server Front End pool that the Survivable Branch Appliance is associated with, by following these steps:
    
      - Click **Start**, click **All Programs**, click **Microsoft Lync Server**, and then click **Lync Server Topology Builder**.
    
      - Expand **Branch Sites**.
    
      - Right-click the Survivable Branch Appliance object to modify, and click **Edit Properties**
    
      - Under Resiliency, select the new Front End pool the Survivable Branch Appliance is to be associated to, and then click **Next**.
    
      - In the console tree, right-click the new Survivable Branch Appliance, click **Topology**, and then click **Publish**.

4.  Restart all Lync Server Services on the Survivable Branch Appliance.

5.  Test the Survivable Branch Appliance. For details, see [Home users on a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md).

6.  Move users from the Lync Server Front End pool at the central site to the Survivable Branch Appliance.

</div>

</div>

<span> </span>

</div>

</div>

</div>

