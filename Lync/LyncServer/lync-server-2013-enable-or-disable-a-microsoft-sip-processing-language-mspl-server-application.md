---
title: 'Lync Server 2013: Enable or disable a Microsoft SIP Processing Language (MSPL) server application'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable or disable a Microsoft SIP Processing Language (MSPL) server application
ms:assetid: b20af38d-224a-4459-991d-0b7eabb3ca7c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182573(v=OCS.15)
ms:contentKeyID: 48185145
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable or disable a Microsoft SIP Processing Language (MSPL) server application in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

You can use Lync Server Control Panel to enable or disable Microsoft SIP Processing Language (MSPL) server applications that run in your Lync Server 2013 environment. These applications are script-only applications that use a scripting language instead of the Microsoft Lync 2013 Preview API.

Not all scripts can be enabled or disabled. For instance, the DefaultRouting script is enabled and this option cannot be changed for DefaultRouting.

<div>

## To enable or disable an MSPL server application

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Topology** and then click **Server Application**.

4.  On the **Server Application** page, click a column heading to sort the applications, if needed, and then click the server application that you want to modify.

5.  Click **Action**.

6.  Click **Enable application** or **Disable application** (that is, if the script supports this option).

</div>

<div>

## See Also


[Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical in Lync Server 2013](lync-server-2013-mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-critical.md)  


[View Microsoft SIP Processing Language (MSPL) server applications in Lync Server 2013](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  


[Managing the Lync Server 2013 topology](lync-server-2013-managing-the-lync-server-topology.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

