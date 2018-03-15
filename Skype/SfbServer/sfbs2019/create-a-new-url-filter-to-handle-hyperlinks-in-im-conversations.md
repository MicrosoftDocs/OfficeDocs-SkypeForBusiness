---
title: "Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d0ee01e5-f039-4a34-ac9d-659fe4e9e879
description: "In addition to modifying the global URL filter, you can configure custom URL filters for individual sites within your Lync Server 2013 deployment. For details about URL filtering, see Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013."
---

# Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations
[]
In addition to modifying the global URL filter, you can configure custom URL filters for individual sites within your Lync Server 2013 deployment. For details about URL filtering, see [Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).
  
### To create a new URL filter

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **IM and Presence**, and then click **URL Filter**.
    
4. On the **URL Filter** page, click **New**.
    
5. In **Select a Site**, click the site for which you want to create the URL filter, and then click **OK**.
    
6. In the **New URL Filter** dialog box, select the **Enable URL Filter** check box to enable URL filtering for the site. 
    
7. To block any active URL that contains a file with an extension listed under **File type extensions to block** in **Edit File Filter**, select the **Block URLs with file extension** check box. 
    
8. In the **Hyperlink prefix** drop-down list box, click the option that corresponds to how you want to handle URLs in instant message conversations. 
    
    The **Allow message** box enables a warning message to be sent to the user when sending hyperlinks that are allowed to be sent. 
    
9. Click **Commit**.
    
## See also

#### 

[Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013](configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)
  
[Create a new file transfer filter in Lync Server 2013 for a specific site](create-a-new-file-transfer-filter-for-a-specific-site.md)
  
[Modify the default file transfer filter in Lync Server 2013](modify-the-default-file-transfer-filter.md)
#### 

[Modify the default URL filter in Lync Server 2013](modify-the-default-url-filter.md)

