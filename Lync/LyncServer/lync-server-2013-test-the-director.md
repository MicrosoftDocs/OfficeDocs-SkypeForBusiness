---
title: 'Lync Server 2013: Test the Director'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Test the Director
ms:assetid: 9627a7e2-28cc-429c-b79b-7c7a27573bb7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398767(v=OCS.15)
ms:contentKeyID: 48184856
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test the Director in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

At this stage, you have a Director or Director pool configured, but your Domain Name System (DNS) SRV entries still point clients to log on by using a pool or Standard Edition server. Before changing the DNS record to make Lync 2013 clients log on automatically by using the Director, test a client by manually pointing it to the Director.

<div>

## To test the deployment

1.  Log on to the computer on which you have the Lync Server Control Panel installed with a domain account that is part of the **CSAdministrator** group.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the navigation pane, click **Topology**, and in the **Status** column confirm that there is a green server with an arrow (that is, ![Server icon with green arrow](images/Gg398767.2263cdb7-7e60-457a-a528-a3a082bd051b(OCS.15).jpg "Server icon with green arrow")) for your Director or Director pool.

4.  Connect two client computers that have the Lync Server 2013 client installed and log on with a different user account enabled for Lync Server 2013 to each computer.

5.  On one of the client computers, click the **Options** menu, select the **Personal** settings group, click **Advanced**, click **Manual Configuration**, and then set the **Internal Server name or IP address** to the fully qualified domain name (FQDN) of the new Director or Director pool.

6.  Log on to both clients and verify that the client logging on by using the Director is able to log on successfully, see the presence status of the other user, and that they can exchange instant messages.

</div>

</div>

<span> </span>

</div>

</div>

</div>

