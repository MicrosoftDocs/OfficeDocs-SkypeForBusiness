---
title: 'Lync Server 2013: Create a new file transfer filter for a specific site'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create a new file transfer filter for a specific site
ms:assetid: d0006487-5217-491c-b730-e6c551cd9825
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182589(v=OCS.15)
ms:contentKeyID: 48185577
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a new file transfer filter in Lync Server 2013 for a specific site

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

In addition to modifying the global file transfer filter, you can configure custom file transfer filters for specific sites within your Lync Server 2013 deployment. For details about file transfer filtering, see [Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

<div>

## To create a file transfer filter for a specific site

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **IM and Presence** and then click **File Filter**.

4.  On the **File Filter** page, click **New**.

5.  In the **Select a Site** dialog box, click the site for which you want to create the file transfer filter, and then click **OK**.

6.  In **New File Filter**, click the **Enable file filter** check box.

7.  In **File transfer** drop-down list box, click **Block All** or **Block specific file types**.

8.  If you clicked **Block All**, skip to step 10.

9.  If you clicked **Block specific file types**, do the following:
    
    1.  Click **Select** to modify the default list of file type extensions that you want to block.
    
    2.  In the **Select File Type** dialog box, select the file types that you want to block or allow by adding or removing their extensions from the categories under **File type extensions**.
    
    3.  If you do not see the extension for a file type that you want to block, type the extension in the text box under **Add file type extensions to the list**, and then click **Add**.
    
    4.  Click **OK**.

10. Click **Commit**.

</div>

<div>

## See Also


[Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)  
[Modify the default file transfer filter in Lync Server 2013](lync-server-2013-modify-the-default-file-transfer-filter.md)  


[Modify the default URL filter in Lync Server 2013](lync-server-2013-modify-the-default-url-filter.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

