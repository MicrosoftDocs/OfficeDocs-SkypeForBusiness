---
title: "Restoring a file store in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 89916fc6-31d3-4c7f-9eaf-c02584761ef4
description: "File Stores for Standard Edition are typically located on the Standard Edition server. File Stores for Enterprise Edition are typically located on a file server or cluster. The following procedure describes how to restore a File Store."
---

# Restoring a file store in Lync Server 2013
[]
File Stores for Standard Edition are typically located on the Standard Edition server. File Stores for Enterprise Edition are typically located on a file server or cluster. The following procedure describes how to restore a File Store.
  
### To restore a File Store

1. If a File Store fails, copy the appropriate File Store from $Backup\ to the File Store location on the file server or Standard Edition server, and then share the folder. 
    
    > [!IMPORTANT]
    > The path and file name for the restored File Store should be exactly the same as the backed up File Store, so that components that use the files can access them. 
  
2. If necessary, set the access control lists (ACLs) for the File Store. At the command line, type:
    
  ```
  Enable-CsTopology
  ```

    > [!NOTE]
    > You need to perform this step only if you have not otherwise run Topology Builder during your restoration process. 
  

