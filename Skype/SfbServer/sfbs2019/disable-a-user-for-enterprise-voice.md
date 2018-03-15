---
title: "Disable a user for Enterprise Voice in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 462002d8-21df-4d77-bf7f-4d059d6a4bb2
description: "Use the following procedure to disable Enterprise Voice for a user account that is enabled for Lync Server 2013."
---

# Disable a user for Enterprise Voice in Lync Server 2013
[]
Use the following procedure to disable Enterprise Voice for a user account that is enabled for Lync Server 2013.
  
### To disable a user account for Enterprise Voice

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.
    
5. In the table, click the user account that you want to enable for Enterprise Voice.
    
6. On the **Edit** menu, click **Show details**.
    
7. On the **Edit Lync Server User** page, under **Telephony**, click any option except **Enterprise Voice**.
    
    > [!NOTE]
    > To restrict a user from making audio or video calls by using Lync, under **Telephony**, click **Audio/video disabled**. 
  
8. Click **Commit**.
    
The user is now unable to use the Enterprise Voice feature.
## See also

#### 

[Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md)
#### 

[Managing Enterprise Voice for users in Lync Server 2013](managing-enterprise-voice-for-users.md)
  
[Lync Server 2013 Management Shell](lync-server-management-shell.md)

