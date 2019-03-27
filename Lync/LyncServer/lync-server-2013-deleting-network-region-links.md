---
title: 'Lync Server 2013: Deleting network region links'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deleting network region links
ms:assetid: 839273cd-d23f-4b38-84e6-d2dc972f49cd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688114(v=OCS.15)
ms:contentKeyID: 49733712
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deleting network region links in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can configure links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Lync Server Control Panel to delete an existing link between two network regions. For details about creating or modifying network region link, see [Configuring network region links in Lync Server 2013](lync-server-2013-configuring-network-region-links.md)

<div>

## To delete a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Link**.

4.  On the **Region Link** page, click the region link that you want to delete.
    
    <div>
    

    > [!NOTE]  
    > You can delete more than one region link at a time. To do this, press CTRL and select multiple region links while holding down the CTRL key. Or, to select all region links, click <STRONG>Select all</STRONG> on the <STRONG>Edit</STRONG> menu.

    
    </div>

5.  From the **Edit** menu, select **Delete**.

6.  Click **OK**.

</div>

<div>

## See Also


[Configuring network region links in Lync Server 2013](lync-server-2013-configuring-network-region-links.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

