---
title: 'Export your topology and copy it to external media for edge installation'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Export your topology and copy it to external media for edge installation
ms:assetid: def9f416-c519-4a72-b242-7d3057d9c1fd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398983(v=OCS.15)
ms:contentKeyID: 48185615
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Export your Lync Server 2013 topology and copy it to external media for edge installation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

After you publish your topology, the Lync Server Deployment Wizard needs access to the Central Management store data in order to start the deployment process on the server. In the internal network, the data is available directly from the servers, but Edge Servers that are not in the internal domain cannot access the data. To make the topology configuration data available for an Edge Server deployment, you must export the topology data to a file and copy it to external media (for example, a USB drive or a network share that is available from the Edge Server) before you run the Lync Server Deployment Wizard on the Edge Server. Use the following procedure to make your topology configuration data available on the Edge Server that you are deploying.

<div>


> [!NOTE]
> After you install Lync Server 2013 on an Edge Server, you manage the Edge Server using the administrative tools in the internal network, which automatically replicate configuration to any Edge Servers in your deployment. The only exception is assigning and installing certificates and stopping and starting services, both of which must be done on the Edge Server.



</div>

<div>

## To make your topology data available on an Edge Server by using Lync Server Management Shell

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  In the Lync Server Management Shell, run the following cmdlet:
    
        Export-CsConfiguration -FileName <ConfigurationFilePath.zip>

3.  Copy the exported file to external media (for example, a USB drive or a network share that is available from the Edge Server during deployment).

</div>

</div>

<span> </span>

</div>

</div>

</div>

