---
title: 'Lync Server 2013: Enabling Office Web Apps Server and Lync Server 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enabling Office Web Apps Server and Lync Server 2013
ms:assetid: 3370ab55-9949-4f32-b88b-5cffed6aaad8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204792(v=OCS.15)
ms:contentKeyID: 48183790
ms.date: 08/19/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring integration with Office Web Apps Server and Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-08-19_

Lync Server 2013 employs Office Web Apps Server to handle PowerPoint presentations. For information about the advantages to this approach, see [Overview of web conferencing in Lync Server 2013](lync-server-2013-web-conferencing-overview.md).

In order to use these new capabilities administrators must install Office Web Apps Server and they must configure Lync Server 2013 to communicate with Office Web Apps Server. This documentation provides information on how to configure Lync Server 2013 to work with Office Web Apps Server. What this documentation does not provide is information on how to install Office Web Apps Server itself; for that information, see the Microsoft Office Web Apps Deployment website at <http://go.microsoft.com/fwlink/p/?linkid=257525>. That guide includes complete prerequisite information for Office Web Apps Server; note that Office Web Apps Server should be installed on a stand-alone computer that is not running Lync Server, Microsoft SQL Server, or any other server application. (You must not have any version of Microsoft Office installed on that computer.) Any computer used to run Office Web Apps Server must also have a specific set of software installed (including .NET Framework 4.5 and Windows PowerShell 3.0); these requirements, along with information on configuring certificates and Internet Information Services (IIS), are discussed in detail in the Microsoft Office Web Apps Deployment website at <http://go.microsoft.com/fwlink/p/?linkid=257525>.

<div>


> [!NOTE]  
> The latest iteration of Office Web Apps Server is named Office Online Server, which is supported by Lync Server 2013. For more detail, refer to the <A href="https://technet.microsoft.com/en-us/library/jj219456(v=office.16).aspx">Office Online Server documentation</A>.



</div>

This document covers the following topic areas:

  - [Configuring Lync Server 2013 to work with Office Web Apps Server](lync-server-2013-configuring-lync-server-2013-to-work-with-office-web-apps-server.md)

  - [Publishing Office Web Apps Server in Lync Server 2013 using a reverse proxy server](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md)

  - [Validating the configuration of Office Web Apps Server in Lync Server 2013](lync-server-2013-validating-the-configuration-of-office-web-apps-server.md)

  - [Configuring clients of Lync Server 2013 for use with Office Web Apps Server](lync-server-2013-configuring-clients-for-use-with-office-web-apps-server.md)

</div>

<span> </span>

</div>

</div>

</div>

