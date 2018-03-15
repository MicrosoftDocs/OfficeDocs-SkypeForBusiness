---
title: "Configure DFS file storage for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a985be20-5a00-4f38-b45b-83dc82de3827
description: "Lync Server 2013 supports using file shares on a Distributed File System (DFS). For details about DFS for Windows Server 2008, see the DFS Step-by-Step Guide for Windows Server 2008 at https://go.microsoft.com/fwlink/p/?linkId=202835.To use a DFS, Lync Server 2013 requires the following:"
---

# Configure DFS file storage for Lync Server 2013
[]
Lync Server 2013 supports using file shares on a Distributed File System (DFS). For details about DFS for Windows Server 2008, see the DFS Step-by-Step Guide for Windows Server 2008 at [https://go.microsoft.com/fwlink/p/?linkId=202835](https://go.microsoft.com/fwlink/p/?linkId=202835).To use a DFS, Lync Server 2013 requires the following:
  
- Namespaces are domain based
    
- All namespace servers are running a minimum of Windows 2008
    
Lync Server 2013 setup requires that permissions on shared folder allow full access to Administrator. Lync Server 2013 will then use NTFS file permissions to ACL the folders. Inherited DFS share permissions will not be used to restrict access. 
  
For more details about File Share requirements, see [File storage support in Lync Server 2013](file-storage-support.md) in the Supportability documentation. 
  
> [!NOTE]
> You may be looking for information on configuring a non-DFS share. If so, check out [Hardware setup for Lync Server 2013](hardware-setup.md). 
  
The following procedure describes how to correctly configure shared folder permissions using the DFS Namespace Wizard (as described in DFS setup guide).
  
### To configure shared folder permissions

1. Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **DFS Management**.
    
2. In the console tree of the DFS Management snap-in, right-click the namespace server (for example filesrv1.contoso.com), and then click **Edit Settings**.
    
3. Select **Shared Folder Permissions**.
    
4. Select **Use Custom Permissions**.
    
5. For the Administrator group, select the following under **Allow**:
    
  - **Full Control**
    
  - **Change**
    
  - **Read**
    
6. Click **Apply**, and then click **OK**.
    

