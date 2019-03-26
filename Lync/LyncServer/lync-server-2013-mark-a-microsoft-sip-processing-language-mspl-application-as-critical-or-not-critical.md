---
title: 'Lync Server 2013: Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical
ms:assetid: df68fdc6-b7e6-4f07-acdc-0cd4c2c888a1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182598(v=OCS.15)
ms:contentKeyID: 48185622
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Microsoft SIP Processing Language (MSPL) server applications are script-only applications that use the MSPL scripting language instead of the Microsoft Lync 2010 API. Some MSPL server applications are specified as critical. If a script is critical, the script must start during system startup in order for Lync Server 2013 to start. If the script fails while Lync Server is running, the server does not shut down, but it stops sending traffic to the script, and it writes errors in the event log.

You can use Lync Server Control Panel to mark Microsoft SIP Processing Language (MSPL) server applications as critical or unmark them.

Not all scripts support this option. For example, the DefaultRouting script is marked as critical, and this option cannot be changed for DefaultRouting.

<div>

## To mark or unmark an MSPL server application as critical

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Topology** and then click **Server Application**.

4.  On the **Server Application** page, click a column heading to sort the applications, if needed, and then click the server application that you want to modify.

5.  Click **Action**.

6.  Click **Mark as critical** or **Unselect as critical** (that is, if the script supports this option).

</div>

<div>

## See Also


[Enable or disable a Microsoft SIP Processing Language (MSPL) server application in Lync Server 2013](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  


[View Microsoft SIP Processing Language (MSPL) server applications in Lync Server 2013](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  


[Managing the Lync Server 2013 topology](lync-server-2013-managing-the-lync-server-topology.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

