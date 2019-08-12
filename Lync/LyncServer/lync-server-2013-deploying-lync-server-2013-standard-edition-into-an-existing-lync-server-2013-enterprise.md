---
title: 'Lync Server 2013: Deploying Lync Server 2013 Standard Edition into an existing Lync Server 2013 Enterprise'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying Lync Server 2013 Standard Edition into an existing Lync Server 2013 Enterprise
ms:assetid: 05ea128d-6c94-49b3-b28b-477367196425
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398112(v=OCS.15)
ms:contentKeyID: 48183297
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying Lync Server 2013 Standard Edition into an existing Lync Server 2013 Enterprise

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

Deploying a Standard Edition server into an existing Enterprise Edition deployment is similar to deploying additional server roles. A Standard Edition server might be deployed to another site, allowing for users in that site to be homed on the Standard Edition server rather than the Front End pool across a wide area network (WAN). The procedures for installing the new site and servers in that site are already defined in other sections of the [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) documentation.

<div id="sectionSection0" class="section">

**To define a new site**

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the console tree, right-click **Lync Server 2013**, and then click **New Central Site**.

3.  On the **Identify the site** page, give a name to the site and optionally enter a description.

4.  Follow the procedures for defining the rest of the site topology. For details, see [Defining and configuring the topology in Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md).

5.  Publish the updated topology. For details, see [Publish the topology in Lync Server 2013](lync-server-2013-publish-the-topology.md).

6.  Set up and install a Standard Edition server.
    
    <div>
    

    > [!Caution]  
    > If you have deployed an environment with only a Standard Edition server, you would have begun the setup process from the Lync Server Deployment Wizard by using the <STRONG>Prepare first Standard Edition server</STRONG> link to install the initial database files to the new Standard Edition server. <STRONG>Do not</STRONG> follow that process when installing a Standard Edition server into an existing Lync Server 2013 deployment.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

