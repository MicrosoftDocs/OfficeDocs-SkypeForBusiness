---
title: 'Lync Server 2013: Install Lync Server server components'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Install Lync Server server components
ms:assetid: 186aed6e-7adf-4a92-9f2e-f9a4de5ff202
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398239(v=OCS.15)
ms:contentKeyID: 48183528
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Install server components for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-05_

Before following these steps, make sure you’re logged onto the server with a domain user account that’s both a local administrator and a member of the RTCUniversalReadOnlyAdmins group in Active Directory.

The Lync Server Deployment Wizard is used to install the needed components for each Lync server role and to activate the server. This article walks you through the steps of deploying a Standard Edition server or a Front End Server in your Lync infrastructure.

<div>

## To install Lync Server components

1.  If the Lync Server Deployment Wizard isn’t running, start it on the server you want to install Lync onto.

2.  Click **Install or Update Lync Server System**.

3.  In the Deployment Wizard, confirm that **Step 1: Install Local Configuration Store** has a green check mark, which means that this server has a local copy of the store installed successfully. If it’s not checked, you need to install the Local Configuration store on the server. Follow the steps at [Install the Local Configuration store in Lync Server 2013](lync-server-2013-install-the-local-configuration-store.md) and then come back here.

4.  When you’re ready to install the Lync Server 2013 components on your server, click **Run** next to **Step 2: Setup or Remove Lync Server Components**.

5.  On the **Set Up Lync Server Components** page, click **Next** to set up components as defined in your published topology.

6.  The **Executing Commands** page will display a summary of commands and installation information as the set up takes place. When it’s done, you can use the list to select a log to view, and then click **View Log**.

7.  When Lync Server 2013 components setup is done, and you’ve reviewed the logs as needed, click **Finish** to complete this step in the installation.
    
    <div>
    

    > [!NOTE]  
    > If you’re prompted to restart the server (which might happen if Windows Desktop Experience needed to be installed), definitely do that. When the computer is back up and running, you need to do these steps over again, starting from step three listed above (basically run Step 2 in the Deployment Wizard one more time).

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

