---
title: 'Create a new URL filter to handle hyperlinks in IM conversations'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create a new URL filter to handle hyperlinks in IM conversations
ms:assetid: d0ee01e5-f039-4a34-ac9d-659fe4e9e879
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182590(v=OCS.15)
ms:contentKeyID: 48185426
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-26_

In addition to modifying the global URL filter, you can configure custom URL filters for individual sites within your Lync Server 2013 deployment. For details about URL filtering, see [Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

<div>

## To create a new URL filter

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **IM and Presence**, and then click **URL Filter**.

4.  On the **URL Filter** page, click **New**.

5.  In **Select a Site**, click the site for which you want to create the URL filter, and then click **OK**.

6.  In the **New URL Filter** dialog box, select the **Enable URL Filter** check box to enable URL filtering for the site.

7.  To block any active URL that contains a file with an extension listed under **File type extensions to block** in **Edit File Filter**, select the **Block URLs with file extension** check box.

8.  In the **Hyperlink prefix** drop-down list box, click the option that corresponds to how you want to handle URLs in instant message conversations.
    
    The **Allow message** box enables a warning message to be sent to the user when sending hyperlinks that are allowed to be sent.

9.  Click **Commit**.

</div>

<div>

## See Also


[Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Create a new file transfer filter in Lync Server 2013 for a specific site](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[Modify the default file transfer filter in Lync Server 2013](lync-server-2013-modify-the-default-file-transfer-filter.md)  


[Modify the default URL filter in Lync Server 2013](lync-server-2013-modify-the-default-url-filter.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

