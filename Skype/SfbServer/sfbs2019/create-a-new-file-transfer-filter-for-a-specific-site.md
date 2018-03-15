---
title: "Create a new file transfer filter in Lync Server 2013 for a specific site"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d0006487-5217-491c-b730-e6c551cd9825
description: "In addition to modifying the global file transfer filter, you can configure custom file transfer filters for specific sites within your Lync Server 2013 deployment. For details about file transfer filtering, see Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013."
---

# Create a new file transfer filter in Lync Server 2013 for a specific site
[]
In addition to modifying the global file transfer filter, you can configure custom file transfer filters for specific sites within your Lync Server 2013 deployment. For details about file transfer filtering, see [Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).
  
### To create a file transfer filter for a specific site

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **IM and Presence** and then click **File Filter**.
    
4. On the **File Filter** page, click **New**.
    
5. In the **Select a Site** dialog box, click the site for which you want to create the file transfer filter, and then click **OK**.
    
6. In **New File Filter**, click the **Enable file filter** check box. 
    
7. In **File transfer** drop-down list box, click **Block All** or **Block specific file types**.
    
8. If you clicked **Block All**, skip to step 10.
    
9. If you clicked **Block specific file types**, do the following:
    
1. Click **Select** to modify the default list of file type extensions that you want to block. 
    
2. In the **Select File Type** dialog box, select the file types that you want to block or allow by adding or removing their extensions from the categories under **File type extensions**.
    
3. If you do not see the extension for a file type that you want to block, type the extension in the text box under **Add file type extensions to the list**, and then click **Add**.
    
4. Click **OK**.
    
10. Click **Commit**.
    
## See also

#### 

[Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)
  
[Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations](create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)
  
[Modify the default file transfer filter in Lync Server 2013](modify-the-default-file-transfer-filter.md)
#### 

[Modify the default URL filter in Lync Server 2013](modify-the-default-url-filter.md)

