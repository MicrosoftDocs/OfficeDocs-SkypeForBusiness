---
title: 'Lync Server 2013: Restoring a file store'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Restoring a file store
ms:assetid: 89916fc6-31d3-4c7f-9eaf-c02584761ef4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202180(v=OCS.15)
ms:contentKeyID: 51541491
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring a file store in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

File Stores for Standard Edition are typically located on the Standard Edition server. File Stores for Enterprise Edition are typically located on a file server or cluster. The following procedure describes how to restore a File Store.

<div>

## To restore a File Store

1.  If a File Store fails, copy the appropriate File Store from $Backup\\ to the File Store location on the file server or Standard Edition server, and then share the folder.
    
    <div>
    

    > [!IMPORTANT]  
    > The path and file name for the restored File Store should be exactly the same as the backed up File Store, so that components that use the files can access them.

    
    </div>

2.  If necessary, set the access control lists (ACLs) for the File Store. At the command line, type:
    
        Enable-CsTopology
    
    <div>
    

    > [!NOTE]  
    > You need to perform this step only if you have not otherwise run Topology Builder during your restoration process.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

