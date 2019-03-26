---
title: 'Lync Server 2013: Create a user policy for Persistent Chat'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create a user policy for Persistent Chat
ms:assetid: aa3774af-d442-4206-8a68-2fbb9102e9d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205170(v=OCS.15)
ms:contentKeyID: 48185103
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a user policy for Persistent Chat in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

In the Lync Server Control Panel, you define user policies that can be assigned to users in **Users**.

The user policy overrides the global policy and site policies, but only for the specific users who are assigned the user policy.

<div>


> [!NOTE]  
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adding Persistent Chat Server to your deployment in Lync Server 2013</A> in the Deployment documentation.<BR>To configure Persistent Chat Server configuration settings, see <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To create a user policy for Persistent Chat

1.  From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.

2.  From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).
    
    <div>
    

    > [!IMPORTANT]  
    > You can also use Windows PowerShell cmdlets. See <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configuring Persistent Chat Server by using Windows PowerShell cmdlets</A> in the Deployment documentation.

    
    </div>

3.  In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.

4.  Click **New**, and then click **User policy**.

5.  In **New Persistent Chat Policy**, do the following:
    
      - In **Name**, specify a name for the new user policy.
    
      - In **Description**, provide details about what the user policy is (for example, Persistent Chat policy for specific user).
    
      - To control Persistent Chat for all users who are not specifically controlled through a user policy, select or clear the **Enable Persistent Chat** check box.

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

