---
title: 'Lync Server 2013: Set up system platforms'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Set up system platforms
ms:assetid: 2e72e49d-2737-4b5b-8c0a-60f6ecb15bf1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204783(v=OCS.15)
ms:contentKeyID: 48183756
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set up system platforms in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Before starting the deployment of Persistent Chat Server, you must install the required operating system on hardware that meets system requirements on servers:

For details about supported hardware for servers running Lync Server 2013, database servers, and file servers, see [Supported hardware for Lync Server 2013](lync-server-2013-supported-hardware.md) in the Supportability documentation. For details about supported operating systems and database software, see [Server software and infrastructure support in Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md) in the Supportability documentation. For details about Windows update requirements, see [Additional server support and requirements in Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md) in the Supportability documentation.

The Persistent Chat Server Front End Server, **PersistentChatService**, can be deployed on one or more stand-alone computers in a Lync Server 2013 Enterprise Edition pool. They cannot be collocated on the Lync Server Enterprise Edition Front End Servers. Persistent Chat Server can be deployed by the Bootstrapper, just like other Lync Server roles. The **Persistent Chat Web Services for File Upload/Download**, and **Persistent Chat Web Services for Chat Room Management** are web components deployed on the Lync Server 2013 Front End Servers.

A single Persistent Chat Server Front End Server can support 20,000 active users. You can have a Persistent Chat Server pool with up to 4 active front ends supporting a total of 80,000 concurrent users. The Persistent Chat Back End Server, **PersistentChatStore**, stores the chat rooms and categories. We recommend that you install the **PersistentChatStore** on a dedicated SQL Server Back End Server in your Enterprise Edition pool; although we support collocating Lync Server 2013 Back End Server and **PersistentChatStore** on the same SQL Server instance.

If your organization requires compliance support, you can install it by using Topology Builder. The Persistent Chat Server Compliance service is installed on the same computer as the Persistent Chat Server Front End Server. A separate database is required for compliance. For details about compliance requirements for Persistent Chat Server, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation.

At a minimum, each topology requires a server with Lync Server 2013 installed and a server with SQL Server database software installed. Topology Builder supports multiple Persistent Chat Server pools. Follow the same deployment instructions for deploying multiple Persistent Chat Server pools as you would for any pool from [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.

You can also deploy Persistent Chat Server with Lync Server 2013 Standard Edition. In this case, the **PersistentChatService** Front End Server is collocated on the Standard Edition server, and you can deploy the **PersistentChatStore** Back End Server on the local SQL Server Express instance.

<div>


> [!IMPORTANT]  
> We do not support Persistent Chat Server&nbsp;Standard Edition for high availability. Performance and scale will be limited. Furthermore, we support only new Persistent Chat Server&nbsp;Standard Edition server deployments. We do not support an upgrade of Lync Server 2010, Group Chat Server to a Lync Server 2013&nbsp;Persistent Chat Server&nbsp;Standard Edition.



</div>

<div>

## See Also


[Additional server support and requirements in Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md)  


[Supported hardware for Lync Server 2013](lync-server-2013-supported-hardware.md)  
[Server software and infrastructure support in Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md)  
[Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)  
[Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

