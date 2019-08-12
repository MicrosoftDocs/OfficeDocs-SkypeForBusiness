---
title: 'Lync Server 2013: Test the Standard Edition server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Test the Standard Edition server
ms:assetid: b6ef67bb-9665-43e4-b8b3-eac8898eebf6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412890(v=OCS.15)
ms:contentKeyID: 48185220
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test the Standard Edition server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The following procedure describes how to test the deployment of a Standard Edition server.

<div>

## To test the deployment of a Standard Edition Server

1.  Use Active Directory Computers and Users to add the Active Directory user object of the administrator role for the Lync Server 2013 deployment (on which Lync Server Control Panel is installed) to the **CSAdministrator** group.

2.  If the user object is currently logged on, log off and then log on again to register the new group assignment.
    
    <div>
    

    > [!NOTE]  
    > The user account cannot be the local administrator of the server running Lync Server 2013, Standard Edition. If you do not add the appropriate users and groups to the CsAdministors group, you will receive an error when opening Lync Server 2013 Control Panel, which states that “Unauthorized: Access is denied due to a role-based access control (RBAC) authorization failure.”

    
    </div>

3.  Use the administrative account to log on to the computer where Lync Server Control Panel is installed.

4.  Start Lync Server Control Panel and provide credentials, if prompted. Lync Server 2013 Control Panel displays deployment information.

5.  In the left navigation bar, click **Topology**, and then confirm that the service status is a computer icon with a green arrow and there is a green check mark next to each Lync Server server role that has been deployed and brought online.

6.  In the left navigation bar, click **Users**, and then enable the two users for Lync Server 2013.

7.  Log one user on to a computer that is joined to the domain, and the other user on to another computer in the domain.

8.  Install Lync Server 2013 on each of the two client computers, and then verify that both users can sign in to Lync Server 2013 and can send instant messages to each other.

</div>

<div>

## See Also


[Deploying clients and devices in Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

