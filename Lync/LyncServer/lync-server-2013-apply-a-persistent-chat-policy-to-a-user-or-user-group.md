---
title: 'Lync Server 2013: Apply a Persistent Chat policy to a user or user group'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Apply a Persistent Chat policy to a user or user group
ms:assetid: 809ef4e0-8d42-4feb-b7c0-3995f39867a7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205038(v=OCS.15)
ms:contentKeyID: 48184652
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Apply a Persistent Chat policy to a user or user group in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

If a user has been enabled for Lync Server 2013, you can apply appropriate policies to specific users to enable or disable them for Persistent Chat Server.

<div>


> [!NOTE]  
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adding Persistent Chat Server to your deployment in Lync Server 2013</A> in the Deployment documentation.<BR>To configure Persistent Chat Server configuration settings, see <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013</A> in the Deployment documentation.



</div>

Use the procedure in this topic to apply a previously created Persistent Chat user policy to one or more user accounts or user groups.

<div>

## To apply a Persistent Chat user policy to a user account

1.  From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.

2.  From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**, and then search on the user account that you want to configure.

4.  In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.

5.  In **Edit Lync Server User** under **Persistent Chat policy**, select the Persistent Chat user policy that you want to apply.
    
    <div>
    

    > [!NOTE]  
    > The <STRONG>&lt;Automatic&gt;</STRONG> settings apply the default effective policy. These settings are applied automatically by the server.

    
    </div>

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

