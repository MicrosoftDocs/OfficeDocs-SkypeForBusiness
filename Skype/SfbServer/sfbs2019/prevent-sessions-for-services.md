---
title: "Prevent sessions for services in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 977dcc5c-2aac-48ef-86a1-a8d47b4d9e74
description: "You can use Lync Server Control Panel to prevent new sessions for all the Lync Server 2013 services running on a specific computer or to prevent new sessions for a specific Lync Server 2013 service."
---

# Prevent sessions for services in Lync Server 2013
[]
You can use Lync Server Control Panel to prevent new sessions for all the Lync Server 2013 services running on a specific computer or to prevent new sessions for a specific Lync Server 2013 service.
  
### To prevent new sessions for all Lync Server services on a computer

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Topology** and then click **Status**.
    
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the services for which you want to prevent new sessions, and then click it. 
    
5. Click **Action**.
    
6. Click **Prevent new sessions for all services**.
    
### To prevent new sessions for a specific service

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Topology** and then click **Status**.
    
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the service you want to start or stop, and then click it. 
    
5. Click **Properties**.
    
6. Sort the list of services, if necessary, and click the service for which you want to prevent new sessions.
    
7. Click **Action**.
    
8. Click **Prevent new sessions for service**.
    
9. Click **Close**.
    
## See also

#### 

[Managing the Lync Server 2013 topology](managing-the-lync-server-2013-topology.md)

