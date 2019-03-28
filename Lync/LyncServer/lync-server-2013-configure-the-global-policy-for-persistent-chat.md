---
title: 'Lync Server 2013: Configure the global policy for Persistent Chat'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure the global policy for Persistent Chat
ms:assetid: 6176eb5c-19de-4c07-bcc0-2e38f8965966
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204951(v=OCS.15)
ms:contentKeyID: 48184323
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure the global policy for Persistent Chat in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

You can use the default global policy by itself to enable Persistent Chat settings for all users in your deployment. You can also specify additional policies for sites and users to control whether Persistent Chat is enabled or disabled for specific users and sites.

You cannot delete the global policy. If you attempt to delete it, the configuration resets to the default values.

<div>


> [!NOTE]  
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adding Persistent Chat Server to your deployment in Lync Server 2013</A> in the Deployment documentation.<BR>To configure Persistent Chat Server configuration settings, see <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To configure the Global Policy for Persistent Chat

1.  From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.

2.  From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md) in the Operations documentation.
    
    <div>
    

    > [!IMPORTANT]  
    > You can also use Windows PowerShell cmdlets. For details, see <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configuring Persistent Chat Server by using Windows PowerShell cmdlets</A> in Deployment documentation.

    
    </div>

3.  In Lync Server Control Panel, click **Persistent Chat**, and then click **Persistent Chat Policy**.

4.  Click **Global** in the list of policies, click **Edit**, and then click **Show details**.

5.  In **Edit Persistent Chat Policy - Global**, do the following:
    
      - In **Name**, specify a new name for the global policy, if you do not want to use the default of Global.
    
      - In **Description**, provide details about what the user policy is (for example, Global policy for centralSiteName).
    
      - To control Persistent Chat for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Enable Persistent Chat** check box.

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

