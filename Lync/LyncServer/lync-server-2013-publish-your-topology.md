---
title: 'Lync Server 2013: Publish your topology'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Publish your topology
ms:assetid: bfed3829-7a54-4b5c-a7cb-28871acd35e7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412935(v=OCS.15)
ms:contentKeyID: 48185287
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Publish your topology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

Each time you use Topology Builder to build your topology, you must publish the topology to a database in the Central Management store so that the data can be used to deploy Lync Server 2013. Use the following procedure to publish your topology.

<div>

## To publish the topology

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In Topology Builder, in the console tree, right-click **Lync 2013**, and then click **Publish Topology**.

3.  On the **Welcome** page of the wizard, click **Next**.

4.  On the **Topology Builder found a CMS store** page, click **Next**.

5.  On the **Create other databases** page, click **Next**.

6.  When the status indicates that database creation succeeded, do the following:
    
      - To view the log, click **View log**.
    
      - To close the wizard, click **Finish**.
        
        <div>
        

        > [!IMPORTANT]  
        > If this is a new installation of an Edge Server or Edge pool, you must export the Edge Server configuration from an existing Front End Server, Front End pool, or Standard Edition server. To export the configuration, see <A href="lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md">Export your Lync Server 2013 topology and copy it to external media for edge installation</A>. You will import the configuration file from the external media or network share during the setup and deployment phase of the Edge Servers through the Lync Server Deployment Wizard.<BR>Once the Edge Servers are operational and the local configuration management store database is replicating with the internal deployment, subsequent updates to the Lync Server 2013 configuration will be published and replicated to the Edge Servers.

        
        </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

