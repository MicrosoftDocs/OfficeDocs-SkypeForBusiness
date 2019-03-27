---
title: 'Prevent new connections to Lync Server for server maintenance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Prevent new connections to Lync Server for server maintenance
ms:assetid: 22b27adf-a590-43bd-9306-a5789ae108d7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520964(v=OCS.15)
ms:contentKeyID: 48183625
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Prevent new connections to Lync Server 2013 for server maintenance

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Lync Server enables you to take a server offline (for example, to apply software or hardware upgrades) without any loss of service to users.

When you specify the option to prevent new connections or calls to a server in a pool, it stops taking any new connections and calls as soon as you implement this option. These new connections and calls are routed through other servers in the pool. A server that is preventing new connections allows its sessions on existing connections to continue until they naturally end. When all existing sessions have ended, the server is ready to be taken offline.

When you prevent new connections to a Front End Server, some Lync Server features and services rely on DNS load balancing to ensure that it functions properly. If you are not using DNS load balancing on the pool, connections through these services may not be re-routed to other servers during the period that the server is preventing new connections, and thus when the server is taken offline some sessions and calls may be interrupted. The features that rely on DNS load balancing to ensure that this option operates properly are as follows:

  - Attendant

  - Conferencing Announcement application

  - Response Group application

  - Announcement application

  - Call Park application

For details about DNS load balancing, see [DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md) in the Planning documentation.

In addition to preventing new connections for all services on a server running Lync Server, you can also prevent new connections for individual Lync Server services. For example, this method is useful in a situation where you need to apply a Lync Server update that does not require the whole server to be shut down. Note that when you prevent connections for one service, you must select a service as it is grouped and displayed in the Windows list of services. For example, the Lync Server Front-End service and the data collection agent for Monitoring are separate Lync Server services, but in the Windows services list they are consolidated and shown as the Lync Server Front End service. You can prevent new connections for the Lync Server Front End service, but you cannot prevent new connections for these two individual underlying Lync Server services separately.

<div>


> [!IMPORTANT]
> When you set a server to prevent new connections, and then restart the server, by default the server will immediately begin accepting new connections after it starts. To prevent this, set the server to only pause and resume manually, before you restart the server.



</div>

<div>

## To prevent new connections to Lync Server:

1.  Log on to the local computer as a member of the Administrators group.

2.  Open the Services snap-in console: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.

3.  In the list, double-click the Lync Server Windows service to which you want to prevent new connections.

4.  In the Properties dialog box, under **Service status: Started**, click **Pause**.

5.  Optionally, but recommended, next to **Startup type**, click **Manual**.
    
    <div>
    

    > [!IMPORTANT]
    > When you set a server to prevent new connections, and then restart the server, by default the server will immediately begin accepting new connections after it starts. To prevent this, set the server to only pause and resume manually, before you restart the server.

    
    </div>

6.  When you are finished, click **OK**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

