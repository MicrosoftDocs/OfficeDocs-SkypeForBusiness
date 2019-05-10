---
title: 'Lync Server 2013: Configure DFS file storage'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure DFS file storage
ms:assetid: a985be20-5a00-4f38-b45b-83dc82de3827
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205150(v=OCS.15)
ms:contentKeyID: 48185037
ms.date: 05/23/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure DFS file storage for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-05-23_

Lync Server 2013 supports using file shares on a Distributed File System (DFS). For details about DFS for Windows Server 2008, see the DFS Step-by-Step Guide for Windows Server 2008 at [http://go.microsoft.com/fwlink/p/?linkId=202835](http://go.microsoft.com/fwlink/p/?linkid=202835).To use a DFS, Lync Server 2013 requires the following:

  - Namespaces are domain based

  - All namespace servers are running a minimum of Windows 2008

Lync Server 2013 setup requires that permissions on shared folder allow full access to Administrator. Lync Server 2013 will then use NTFS file permissions to ACL the folders. Inherited DFS share permissions will not be used to restrict access.

For more details about File Share requirements, see [File storage support in Lync Server 2013](lync-server-2013-file-storage-support.md) in the Supportability documentation.

<div>


> [!NOTE]  
> You may be looking for information on configuring a non-DFS share. If so, check out <A href="lync-server-2013-hardware-setup.md">Hardware setup for Lync Server 2013</A>.



</div>

The following procedure describes how to correctly configure shared folder permissions using the DFS Namespace Wizard (as described in DFS setup guide).

<div>

## To configure shared folder permissions

1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **DFS Management**.

2.  In the console tree of the DFS Management snap-in, right-click the namespace server (for example filesrv1.contoso.com), and then click **Edit Settings**.

3.  Select **Shared Folder Permissions**.

4.  Select **Use Custom Permissions**.

5.  For the Administrator group, select the following under **Allow**:
    
      - **Full Control**
    
      - **Change**
    
      - **Read**

6.  Click **Apply**, and then click **OK**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

