---
title: "Export your Lync Server 2013 topology and copy it to external media for edge installation"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: def9f416-c519-4a72-b242-7d3057d9c1fd
description: "After you publish your topology, the Lync Server Deployment Wizard needs access to the Central Management store data in order to start the deployment process on the server. In the internal network, the data is available directly from the servers, but Edge Servers that are not in the internal domain cannot access the data. To make the topology configuration data available for an Edge Server deployment, you must export the topology data to a file and copy it to external media (for example, a USB drive or a network share that is available from the Edge Server) before you run the Lync Server Deployment Wizard on the Edge Server. Use the following procedure to make your topology configuration data available on the Edge Server that you are deploying."
---

# Export your Lync Server 2013 topology and copy it to external media for edge installation
[]
After you publish your topology, the Lync Server Deployment Wizard needs access to the Central Management store data in order to start the deployment process on the server. In the internal network, the data is available directly from the servers, but Edge Servers that are not in the internal domain cannot access the data. To make the topology configuration data available for an Edge Server deployment, you must export the topology data to a file and copy it to external media (for example, a USB drive or a network share that is available from the Edge Server) before you run the Lync Server Deployment Wizard on the Edge Server. Use the following procedure to make your topology configuration data available on the Edge Server that you are deploying.
  
> [!NOTE]
> After you install Lync Server 2013 on an Edge Server, you manage the Edge Server using the administrative tools in the internal network, which automatically replicate configuration to any Edge Servers in your deployment. The only exception is assigning and installing certificates and stopping and starting services, both of which must be done on the Edge Server. 
  
### To make your topology data available on an Edge Server by using Lync Server Management Shell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. In the Lync Server Management Shell, run the following cmdlet:
    
  ```
  Export-CsConfiguration -FileName <ConfigurationFilePath.zip>
  ```

3. Copy the exported file to external media (for example, a USB drive or a network share that is available from the Edge Server during deployment).
    

