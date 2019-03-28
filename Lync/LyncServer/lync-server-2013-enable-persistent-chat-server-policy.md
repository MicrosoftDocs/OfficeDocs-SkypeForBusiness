---
title: 'Lync Server 2013: Enable Persistent Chat Server policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable Persistent Chat Server policy
ms:assetid: 87063d6c-2e38-4970-b76d-2aa15f0de29e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205056(v=OCS.15)
ms:contentKeyID: 48184718
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable Persistent Chat Server policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

In the Lync Server 2013 Control Panel, you can use the **Persistent Chat Policy** page of the **Persistent Chat** group to manage policies at a global, pool, site, or user level, including configuring the default global policy and creating one or more additional user and site policies for your deployment. If a user is enabled for Persistent Chat Server by policy, then the Persistent Chat Server environment appears in their Lync 2013 client.

<div>


> [!NOTE]  
> In the topology, Persistent Chat Server site policies apply globally, per user’s pool, or per user’s site, or per user.



</div>

The global policy is created automatically when you deploy Persistent Chat Server, and it can be configured, but not deleted. Because the global policy applies to all users, it doesn’t have to be set per user.

You can create and configure multiple site and user policies which, together with the global policy, enable users for Persistent Chat Server. Pool and site Persistent Chat Server policies override the global Persistent Chat Server policy, but only for users of that site. User policies override both global, pool, and site policies for the users to whom the user policy is assigned.

<div>


> [!NOTE]  
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adding Persistent Chat Server to your deployment in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## In This Section

  - [Configure the global policy for Persistent Chat in Lync Server 2013](lync-server-2013-configure-the-global-policy-for-persistent-chat.md)

  - [Create a site policy for Persistent Chat in Lync Server 2013](lync-server-2013-create-a-site-policy-for-persistent-chat.md)

  - [Create a user policy for Persistent Chat in Lync Server 2013](lync-server-2013-create-a-user-policy-for-persistent-chat.md)

  - [Apply a Persistent Chat policy to a user or user group in Lync Server 2013](lync-server-2013-apply-a-persistent-chat-policy-to-a-user-or-user-group.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

