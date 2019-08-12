---
title: 'Lync Server 2013: Configuring the primary management server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring the primary management server
ms:assetid: 44e2e9a8-c130-4c66-9871-80b1ff11b27c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204844(v=OCS.15)
ms:contentKeyID: 48183986
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring the primary management server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-19_

In order to take full advantage of the new health monitoring capabilities included in Microsoft Lync Server 2013 administrators must first designate a computer to act as your primary management server; on that computer you must then install System Center Operations Manager 2007 R2 or System Center Operations Manager 2012. In addition, you must install a supported version of SQL Server to function as your Operations Manager back-end database. If you are using System Center Operations Manager 2012 you can use any of the following versions of SQL Server as your back-end database:

  - SQL Server 2008 R2 Service Pack 1

  - SQL Server 2008 R2 Service Pack 2

If you are using System Center Operations Manager 2007 R2 it is recommended that you install either SQL Server 2005 Service Pack 4 or SQL Server 2008 Service Pack 3. You can also use SQL Server 2008 R2 as the backend database for System Center Operations Manager 2007 R2. See Appendix 1 of this documentation for more information on configuring SQL Server 2008 R2 to work with System Center Operations Manager 2007 R2.

When you install System Center Operations Manager 2012 or System Center Operations Manager 2007 R2 you need to install all the components of that product, including:

  - Operational database

  - Server

  - Console

  - Windows PowerShell cmdlets

  - Web console

  - Reporting

  - Data warehouse

These components and their installation will not be discussed in detail in this document. For details about System Center Operations Manager 2007 R2, see the Operations Manager 2007 R2 documentation at <http://go.microsoft.com/fwlink/p/?linkid=257526> and the System Center Operations Manager 2012 documentation at <http://go.microsoft.com/fwlink/p/?linkid=257527>. You should follow those instructions if you are going to use SQL Server 2005 or SQL Server 2008 Service Pack 1 as your back-end database.

If you are using System Center Operations Manager 2012 then you can use SQL Server 2012 as your back-end database. For details about SQL Server 2012, see Books Online for SQL Server 2012 at [http://go.microsoft.com/fwlink/p/?LinkId=257528](http://go.microsoft.com/fwlink/p/?linkid=257528).

Keep in mind that you can only have a single Primary Management Server per Lync Server deployment. Also, while you can use either System Center Operations Manager 2012 or System Center Operations Manager 2007 R2, you cannot run the two applications simultaneously—you must choose one or the other. For example, if you are running System Center Operations Manager 2012 then all your System Center agents must also be running System Center Operations Manager 2012. You cannot have some agents running System Center Operations Manager 2012 and other agents running System Center Operations Manager 2007 R2.

</div>

<span> </span>

</div>

</div>

</div>

