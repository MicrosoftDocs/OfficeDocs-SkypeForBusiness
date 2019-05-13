---
title: 'Lync Server 2013: Start or stop Lync Server services'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Start or stop Lync Server 2013 services
ms:assetid: 1c70b4ec-9de5-4f7a-a3c9-c0eb76710505
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520958(v=OCS.15)
ms:contentKeyID: 48183554
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Start or stop Lync Server 2013 services

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

You can use Lync Server Control Panel to start or stop all the Lync Server 2013 services running on a specific computer or to start or stop a specific service.

<div>

## To start or stop all Lync Server services on a computer

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. You can determine whether you have been assigned the CsServerAdministrator or the CsAdministrator RBAC role by running a command similar to the following:
    
        Get-CsAdminRoleAssignment -Identity "kenmyer"

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Topology** and then click **Status**.

4.  On the **Status** page, sort or search through the list as needed to find the computer that is running the services you want to start or stop, and then click it.

5.  Click **Action**.

6.  Click **Start All services** or **Stop All services**.

</div>

<div>

## To start or stop a specific service

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Topology** and then click **Status**.

4.  On the **Status** page, sort or search through the list as needed to find the computer that is running the service you want to start or stop, and then click it.

5.  Click **Properties**.

6.  Sort the list of services, if necessary, and click the service you want to start or stop.

7.  Click **Action**.

8.  Click **Start service** or **Stop service**.

9.  Click **Close**.

</div>

<div>

## See Also


[Prevent sessions for services in Lync Server 2013](lync-server-2013-prevent-sessions-for-services.md)  


[Managing the Lync Server 2013 topology](lync-server-2013-managing-the-lync-server-topology.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

