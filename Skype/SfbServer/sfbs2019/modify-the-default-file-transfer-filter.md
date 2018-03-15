---
title: "Modify the default file transfer filter in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 791774a2-0bb6-4b5b-aeb0-ff69abb170f4
description: "Lync Server 2013 provides a global file transfer filter that blocks specific types of files during the following file-related activities within your Lync Server 2013 deployment:"
---

# Modify the default file transfer filter in Lync Server 2013
[]
Lync Server 2013 provides a global file transfer filter that blocks specific types of files during the following file-related activities within your Lync Server 2013 deployment:
  
- File transfer requests during instant messaging (IM) conversations
    
- File uploads and downloads while using the handout feature in the Office Live Meeting 2007 client
    
- Multimedia playback during conferences
    
Depending on the types of files you want to block or allow, you can use Lync Server Control Panel to modify the global filter. For details about file transfer filtering, see [Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).
  
### To modify the default file transfer filter

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **IM and Presence** and then click **File Filter**.
    
4. On the **File Filter** page, double-click the **Global** filter. 
    
5. In **Edit File Filter**, select the **Enable file filter** check box. 
    
6. In the **File transfer** drop-down list box, click **Block All** or **Block specific file types**.
    
7. If you clicked **Block All**, skip to step 9.
    
8. If you clicked **Block specific file types**, do the following:
    
1. Click **Select** to modify the default list of file type extensions that you want to block. 
    
2. In **Select File Type**, select the file types that you want to block or allow by adding or removing their extensions from the categories under **File type extensions**.
    
3. If you do not see the extension for a file type that you want to block, type the extension in the text box under **Add file type extensions to the list**, and then click **Add**.
    
4. Click **OK**.
    
9. Click **Commit**.
    
## See also

#### 

[Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)
  
[Create a new file transfer filter in Lync Server 2013 for a specific site](create-a-new-file-transfer-filter-for-a-specific-site.md)
  
[Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations](create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)
#### 

[Modify the default URL filter in Lync Server 2013](modify-the-default-url-filter.md)

