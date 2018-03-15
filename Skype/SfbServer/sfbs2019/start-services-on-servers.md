---
title: "Start services on servers for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fa26eaed-0529-4f32-9f3f-f32c4bd4b1c8
description: "To successfully complete this procedure you should be logged in as a user who is a member of the RTCUniversalServerAdmins group or have the correct permissions delegated. For details about delegating permissions, see the topic Delegate setup permissions in Lync Server 2013."
---

# Start services on servers for Lync Server 2013
[]
To successfully complete this procedure you should be logged in as a user who is a member of the RTCUniversalServerAdmins group or have the correct permissions delegated. For details about delegating permissions, see the topic [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
  
After you install the Local Configuration store on your servers, install the Lync Server 2013 components, and configure certificates on a Front End Server or Front End Server, you must start the Lync Server 2013 services on the server. Use the following procedure to start services on each Front End Server in your deployment.
  
### To start services on a Standard Edition or Front End Server

1. In the Lync Server Deployment Wizard, on the **Lync Server 2013** page, click **Run** next to **Step 4: Start Services**.
    
2. On the **Start Services** page, click **Next** to start the Lync Server services on the server. 
    
3. On the **Executing Commands** page, after all services have started successfully, click **Finish**.
    
    > [!IMPORTANT]
    > The command to start the services on the server is a best effort method to report that the services have in fact started. It might not reflect the actual state of the service. We recommend that you use the step **Service Status (Optional)** immediately following **Start Services** to open the Microsoft Management Console (MMC) and confirm that the services have started successfully. If any Lync Server service has not started, you can right-click that service in the MMC, and then click **Start**. 
  

