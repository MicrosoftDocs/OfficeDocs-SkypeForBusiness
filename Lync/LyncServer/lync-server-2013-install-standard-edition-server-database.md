---
title: 'Lync Server 2013: Install Standard Edition server database'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Install Standard Edition server database
ms:assetid: 0bd3a804-aad6-48cb-981b-54725af032db
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398167(v=OCS.15)
ms:contentKeyID: 48183385
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Install Standard Edition server database for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

Setting up a Standard Edition server as the only server in your infrastructure that homes users differs from other server installations in that there is a selection in the **Deployment Wizard** specifically for setting up the initial server.

<div>

## To install a Standard Edition server

1.  Log on to the server where you are going to install Standard Edition server as a local administrator or a domain equivalent.

2.  If you have not prepared Active Directory Domain Services, then first perform those procedures. For details, see [Preparing Active Directory Domain Services for Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md).

3.  In the Lync Server Deployment Wizard, click **Prepare first Standard Edition server**.

4.  On the **Prepare single Standard Edition Server** page, click **Next**.

5.  On the **Executing Commands** page, the SQL Server 2012 Express is installed as the Central Management store. Necessary firewall rules are created. When the installation of the database and prerequisite software is completed, click **Finish**.
    
    <div>
    

    > [!NOTE]  
    > The initial installation may take some time with no visible updates to the command output summary screen. This is due to the installation of the SQL Server Express. If you need to monitor the installation of the database, use Task Manager to monitor the setup.

    
    </div>

6.  On the Lync Server Deployment Wizard page, click **Install Topology Builder** if you have not previously installed the administrative tools. For details, see [Install Lync Server 2013 administrative tools](lync-server-2013-install-lync-server-administrative-tools.md).

7.  Confirm that there are green check marks next to “Prepare Active Directory,” “Prepare first Standard Edition server,” and “Install Topology Builder.”

</div>

</div>

<span> </span>

</div>

</div>

</div>

